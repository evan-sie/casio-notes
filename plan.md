# Casio AI — Class Context System: Implementation Plan

## AGENT BRIEFING

You are an AI assistant executing a code modification task on a Raspberry Pi Zero running a
Python-based engineering tutor application (`casio_ai.py`). Read this entire document before
touching any file. Your job is to implement the class context selection system described below.
Do not refactor unrelated code. Do not change any behavior not explicitly mentioned here.

The file you are modifying (`casio_ai.py`) may differ slightly from what this plan was written
against — it is a near-current backup. Read the actual file on disk first, understand its
structure, then apply these changes with good judgment. The descriptions below tell you what
to build and why; you are trusted to write the correct implementation.

---

## What This System Does

The user studies multiple engineering classes (Statics, Dynamics, Thermodynamics, etc.).
Each class has a Markdown summary file (`.md`) containing the professor's specific variable
notation, methods, and formulas. These files live in `~/notes/` on the Pi, synced from a
GitHub repo via `download_notes.sh`.

The boot sequence works as follows:

```
1. Existing splash screen (functions / keyboard map) — unchanged
2. Class selector menu — user picks a class or presses F2 to skip entirely
3. Main chat window opens as normal
4. If a class was selected: an in-chat confirmation line appears immediately,
   styled like the F6 restart warning, asking the user to confirm or skip the upload
5. User confirms → the .md is sent to Gemini as the first chat message
   Gemini responds → chat shows: "Context Loaded. Course: [class name]"
   User skips → chat shows: "Context skipped. Running in general mode." and the
   F1_PROMPT reverts to its original behavior (no session context reminder active)
```

The key design principle: the user is never blocked waiting for a network call before
entering the chat window. The upload confirmation and the actual API call both happen
inside the main chat loop, using the same in-chat messaging pattern as F6 restart.

If the user skips class selection entirely at step 2, steps 4 and 5 are skipped completely
and the app behaves exactly as it did before this feature was added.

---

## File Layout

```
GitHub repo: casio-notes (user-managed, do not create or modify)
  statics.md, dynamics.md, aerodynamics.md, (etc.)

Pi filesystem:
  ~/notes/            <- synced from GitHub, read-only at runtime
  ~/calc-main/
    casio_ai.py       <- MODIFY THIS
    download_notes.sh <- CREATE THIS (git sync helper)
```

---

## Task 1 — Create `download_notes.sh`

Create a small bash script at `~/calc-main/download_notes.sh`. Its job is to `git clone`
the casio-notes repo into `~/notes/` on first run, and `git pull` on subsequent runs.
Include a placeholder for the repo URL with a clear comment telling the user to fill it in.
Make the script executable after creating it.

---

## Task 2 — Modify `casio_ai.py`

Read the actual file on disk carefully before making any changes. The sections below describe
each change as intent — implement them correctly for the state of the file you find.

### 2a. Configuration constant

Add a `NOTES_DIR` constant in the USER CONFIGURATION block, resolving to `~/notes/` via
`os.path.expanduser`.

### 2b. Global state additions

In the GLOBAL STATE section, add two new variables alongside the existing globals:
- `active_class_name` — initially `None`. Stores the name of the selected class for the session.
- `context_confirm_active` — initially `False`. Mirrors the pattern of `restart_confirm_active`;
  set to `True` when the in-chat upload confirmation is waiting for user input.
- `pending_class_md` — initially `None`. Holds the `.md` file content between class selection
  and the user confirming the upload inside the chat window.

### 2c. `F1_PROMPT` — append session context reminder

Find where `F1_PROMPT` closes and insert the following block immediately before the closing
tag. Do not alter any existing text in the prompt — only append this new XML section:

```
<session_context_reminder>
CRITICAL SESSION INSTRUCTION: At the start of this session, you were provided with
class-specific methods, variable notation, and formulas for this course. These take
absolute priority over any general engineering conventions. When solving the problem above:
- Use ONLY the variable names from the session context. Do not rename or substitute them.
- Apply the specific methods and formula forms from the session context.
- If the session method differs from a general textbook approach, always use the session method.
- If no session context was loaded, solve using standard mechanical engineering conventions.
</session_context_reminder>
```

### 2d. Class selector UI function

Add a new curses function that presents a navigable list of `.md` files found in `NOTES_DIR`.
The user moves up/down through the list and presses Enter to select. F2 skips selection
entirely. The function returns `(class_name, md_content)` on selection, or `(None, None)`
if skipped or if the notes directory doesn't exist or is empty.

Style it consistently with the existing splash screens — same centered title format, same
`STYLES` keys, a footer hint line showing the available keys. Set `stdscr.timeout(-1)` for
blocking input while the selector is open, and restore it to `50` before returning regardless
of exit path (use a `finally` block).

Place this function in the splash screen section of the file.

### 2e. Context upload function

Add a function that takes `(class_name, md_content, width)` — no `stdscr` argument since
it runs inside the main loop — and sends the class notes to Gemini as the first chat message.

The message it sends must use exactly this structure (substitute `{class_name}` and
`{md_content}` at call time):

```
<class_context>
You are being initialized for a {class_name} engineering problem-solving session.
The following document contains the exact methods, variable notation, and formulas
used in this course. Read it carefully and completely.

---
{md_content}
---

</class_context>

<initialization_instruction>
For this entire session you MUST:
1. Use ONLY the variable names and notation defined in the document above.
   If the course uses a specific symbol for a quantity, use that symbol — no substitutions.
2. Apply the specific methods and formula forms shown above, not general textbook alternatives.
3. When the class method and a general method differ, always default to the class method.
4. Treat this context as your ground truth for this subject.

Respond ONLY with this exact confirmation line and nothing else:
"Context Loaded. Course: {class_name}"
</initialization_instruction>
```

The function should handle its own threading (same pattern as `processing_task` — spin up a
worker thread, animate a throbber in the status line while waiting, then replace it with the
result). On success display Gemini's confirmation in `diag_ok` style. On failure display an
error in `diag_crit` style.

### 2f. Wire class selector into `main()` startup

After `show_splash_system()` returns and before the main loop begins, call
`show_class_selector`. If the user selected a class, store the name in `active_class_name`
and the content in `pending_class_md`, and set `context_confirm_active = True`. Add a header
line showing the active class name (bold, using the `mode_alpha` style). If the user skipped
selection entirely, add a header line reading "Class: None" in normal style and do not set
`context_confirm_active`.

### 2g. Wire confirmation into the main input loop

In the main `while True:` input loop, immediately after the existing `restart_confirm_active`
cancellation logic, add handling for `context_confirm_active`:

**When `context_confirm_active` is True and any key is pressed:**
- On Enter (`KEY_ENTER` / 10): confirm the upload. Clear `context_confirm_active`. Call the
  context upload function with `active_class_name` and `pending_class_md`. Set
  `pending_class_md = None` after the call.
- On Escape (key 27) or F2: skip the upload. Clear `context_confirm_active`. Set
  `pending_class_md = None` and `active_class_name = None`. Update the header line to read
  "Class: None (skipped)". Append a chat line: "Context skipped. Running in general mode."
- All other keys while confirmation is active: consume and ignore (do not process as normal
  input), the confirmation message stays visible.

**Showing the confirmation prompt:**
Immediately after entering the chat window (after `add_splash_hint_line()` and after
`context_confirm_active` has been set), if `context_confirm_active` is True, append a chat
history line styled like the F6 warning (`diag_crit` or a suitable attention style) reading:

```
[?] Press Enter to load [class_name] context, or Esc to skip
```

This line should auto-scroll into view the same way the F6 confirmation does.

---

## Task 3 — Verification Checklist

Run each check and report pass/fail. Do not declare the task complete if any item fails.

1. Parse check: `python3 -c "import ast; ast.parse(open('casio_ai.py').read()); print('Syntax OK')"` — must print `Syntax OK`.
2. `NOTES_DIR` constant exists in the USER CONFIGURATION block.
3. `active_class_name`, `context_confirm_active`, and `pending_class_md` exist in the GLOBAL STATE block.
4. `<session_context_reminder>` block exists inside `F1_PROMPT`.
5. `show_class_selector` function exists and is called from `main()` before the main loop.
6. Context upload function exists and is called when the user confirms in-chat.
7. Enter confirms and Esc/F2 skips the upload, both clearing `context_confirm_active`.
8. `download_notes.sh` exists at `~/calc-main/download_notes.sh` and is executable.

---

## Implementation Notes

- Installed packages: `google-genai`, `curses`, `PIL`, `cv2`. Do not install anything new.
- All `stdscr.addstr` calls must be wrapped in `try/except curses.error`.
- `STYLES` keys safe to use: `normal`, `bold`, `diag_ok`, `diag_crit`, `status_text`,
  `splash_title`, `mode_alpha`.
- The context upload is intentionally threaded like `processing_task` — it makes a blocking
  network call and must not freeze the UI.
- The `restart_confirm_active` variable and its handling in the main loop is the direct
  reference pattern for `context_confirm_active`. Study how F6 works before implementing.
- The version of `casio_ai.py` on disk is authoritative. If anything here conflicts with
  what you see in the file, use your judgment and flag the discrepancy in your report.
