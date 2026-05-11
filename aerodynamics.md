# MECH 4v95 Aerodynamics (Spring 2026) - Course Reference

Course taught by Prof. Edward B. White. Lecture Packs: A (Aerodynamics and Aircraft), B (Governing Equations / Control Volumes), C (Ideal-Gas Thermodynamics), D (Supersonic Flow), E (Quasi-1D Nozzles), G (Potential Flow / Incompressible), H (Airfoils / Thin-Airfoil Theory). Pack F is not used in this section. All math below is plain text per AI constraints.

---

## 1. Variable Notation

### Aircraft, Geometry, and Coefficients (Lec A)
  L - Lift force, 3D (N or lbf)
  L_prime - Lift per unit span, 2D sectional lift (N/m or lbf/ft)
  D - Drag force, 3D (N or lbf)
  D_prime - Drag per unit span, 2D sectional drag (N/m or lbf/ft)
  m - Pitching moment, 3D (N*m or ft*lbf)
  m_prime - Pitching moment per unit span, 2D (N*m/m or ft*lbf/ft)
  W - Weight (N or lbf)
  T - Thrust (N or lbf) [context-dependent; also static temperature]
  q_inf - Freestream dynamic pressure (Pa or psf)
  U_inf - Freestream velocity (m/s or ft/s)
  V - Velocity magnitude (m/s); also context: specific volume
  p - Static pressure (Pa or psf)
  p_inf - Freestream static pressure (Pa or psf)
  p_0 - Stagnation (total) pressure (Pa)
  rho - Density (kg/m^3 or slug/ft^3)
  rho_inf - Freestream density (kg/m^3)
  rho_0 - Stagnation density (kg/m^3)
  S_ref - Reference (planform) wing area (m^2 or ft^2)
  S_wet - Wetted surface area (m^2 or ft^2)
  S_wing - Wing area, same as S_ref (m^2 or ft^2)
  S_tail - Tail reference area (m^2 or ft^2)
  S_flapped - Wing area whose span includes a high-lift device (m^2)
  b - Wingspan (m or ft)
  c - Chord length (m or ft)
  c_bar - Mean aerodynamic chord (m or ft)
  c_root - Root chord (m or ft)
  c_tip - Tip chord (m or ft)
  AR - Aspect ratio (dimensionless), AR = b^2/S_ref
  lambda - Taper ratio = c_tip/c_root (dimensionless)
  Lambda - Sweep angle (degrees or radians)
  Lambda_LE - Leading-edge sweep angle (degrees or radians)
  Lambda_hinge - Hinge-line sweep angle (degrees)
  Gamma_geom - Dihedral angle (degrees)
  ell_t - Tail length, distance between wing AC and horizontal-tail AC (m or ft)
  alpha - Angle of attack (radians in equations; degrees in plots)
  alpha_L0 - Zero-lift angle of attack (radians or degrees)
  alpha_t - Total angle of attack for rocket-style problems (radians)
  beta - Sideslip angle (radians or degrees)
  phi - Roll angle (radians or degrees)
  z(x) - Camber line (m); locus midway between top and bottom surfaces
  t(x) - Thickness distribution (m), surface-to-surface normal to chord
  C_L - 3D lift coefficient (dimensionless)
  C_D - 3D drag coefficient (dimensionless)
  C_m - 3D pitching moment coefficient (dimensionless)
  C_L_max - Maximum 3D lift coefficient (dimensionless)
  C_D_0 - Zero-lift drag coefficient (dimensionless)
  C_D_i - Induced drag coefficient (dimensionless)
  c_l - 2D sectional lift coefficient (dimensionless), per unit span
  c_d - 2D sectional drag coefficient (dimensionless), per unit span
  c_m - 2D sectional pitching moment coefficient (dimensionless)
  c_l_max - Maximum 2D sectional lift coefficient (dimensionless)
  C_p - Pressure coefficient (dimensionless)
  C_f - Skin-friction coefficient (dimensionless), typical 0.003-0.005
  e - Oswald efficiency factor (dimensionless), near 1.0 but not exceeding
  e_span - Span efficiency factor (dimensionless), near 1.0
  V_stall - Stall speed (m/s)
  W/S_ref - Wing loading (N/m^2 or lbf/ft^2)
  Delta_C_L_device - Lift increment due to high-lift device (dimensionless)
  AC - Aerodynamic center (location, in units of chord)
  CP - Center of pressure (location, in units of chord)
  MRC - Moment reference center (location)
  N - Normal force in body-fixed frame (N or lbf)
  A - Axial force in body-fixed frame (N or lbf); also area
  Y_b - Side force in body-fixed frame (N or lbf)
  Y_w - Side force in wind-fixed frame (N or lbf)
  ell_b - Roll moment, body-fixed (N*m)
  m_b - Pitch moment, body-fixed (N*m)
  n_b - Yaw moment, body-fixed (N*m)

### Governing Equations and Conservation Laws (Lec B)
  u, v, w - Velocity components in x, y, z directions (m/s)
  V_vec - Velocity vector (u, v, w) (m/s)
  n_hat - Outward-pointing surface-normal unit vector (dimensionless)
  m_sys - Mass of a system of particles (kg)
  m_dot - Mass flow rate (kg/s)
  E - Total energy per unit mass (J/kg)
  e - Specific internal energy (J/kg); e(T) = Cv*T + e_ref
  e_ref - Reference internal energy (J/kg)
  h - Specific enthalpy (J/kg); h(T) = Cp*T + h_ref
  h_ref - Reference enthalpy (J/kg)
  Q_dot - Heat addition rate (W)
  W_dot - Work rate (W)
  mu_visc - Dynamic viscosity (Pa*s or slug/(ft*s))
  tau_visc - Viscous shear stress (Pa)
  g - Gravitational acceleration (9.81 m/s^2)
  z - Vertical position (m); also camber line
  Re - Reynolds number (dimensionless)
  Re_c - Chord-based Reynolds number (dimensionless), Re_c = rho*U_inf*c/mu_visc
  Re_d - Diameter-based Reynolds number (dimensionless)
  Fr - Froude number (dimensionless)
  M - Mach number (dimensionless), M = V/a
  Dq_Dt - Material (substantial) derivative of quantity q
  F_body - Body force vector (N)
  F_surface - Surface force vector (N)
  F_A_doubleprime - Net force on unknown-stress surfaces (N)

### Ideal-Gas Thermodynamics (Lec C)
  R - Specific gas constant (J/(kg*K)). Air: R = 287
  R_u - Universal gas constant = 8314 J/(kmol*K)
  M_mol - Molecular mass (kg/kmol). Air: M_mol ~ 29
  Cv - Specific heat at constant volume (J/(kg*K)). Air: Cv ~ 718
  Cp - Specific heat at constant pressure (J/(kg*K)). Air: Cp ~ 1005
  gamma - Ratio of specific heats Cp/Cv. Air: gamma = 1.4
  s - Specific entropy (J/(kg*K))
  delta_q - Specific heat addition (J/kg)
  delta_w_visc - Specific viscous work (J/kg)
  upsilon - Specific volume = 1/rho (m^3/kg)
  T_0 - Stagnation (total) temperature (K)
  a - Local speed of sound (m/s); a = sqrt(gamma*R*T)
  a_0 - Stagnation sound speed (m/s)
  a_star - Critical sound speed at M=1 (m/s); a_star/a_0 ~ 0.913 for gamma=1.4
  V_star - Critical velocity = a_star (m/s)

### Supersonic Flow (Lec D)
  mu_mach - Mach angle (radians or degrees); mu_mach = arcsin(1/M)
  theta - Oblique shock wave angle (degrees), measured from upstream flow
  delta - Flow deflection (turning) angle through oblique shock (degrees)
  M1, M2 - Upstream and downstream Mach numbers
  M1_n - Normal component of upstream Mach across oblique shock
  M2_n - Normal component of downstream Mach across oblique shock
  M1_t - Tangential component of upstream Mach across oblique shock
  M2_t - Tangential component of downstream Mach across oblique shock
  u1, u2 - Normal velocity components across oblique shock (m/s)
  w1, w2 - Tangential velocity components across oblique shock (m/s); w1=w2
  p_bot, p_top - Static pressure on bottom and top of supersonic airfoil (Pa)
  M_bot, M_top - Mach number on bottom and top of supersonic airfoil
  alpha_pm - Prandtl-Meyer expansion turn angle (radians or degrees)
  nu_pm - Prandtl-Meyer function (radians or degrees)

### Quasi-1D Nozzles (Lec E)
  A - Cross-sectional area (m^2)
  A_star - Sonic (throat) area where M = 1 (m^2)
  A_throat - Actual minimum (geometric) throat area (m^2)
  A_exit - Nozzle exit area (m^2)
  p_exit - Static pressure at nozzle exit (Pa)
  p_star - Static pressure at M=1 (Pa)
  m_dot_choked - Choked mass flow rate (kg/s)

### Potential Flow / Incompressible (Lec G)
  phi - Velocity potential (m^2/s); v_vec = grad(phi)
  psi - Streamfunction (m^2/s)
  Omega - Fluid element rotation rate (1/s)
  omega - Vorticity (1/s); omega = curl(v_vec); 2D: omega = dv/dx - du/dy
  Gamma_circ - Circulation (m^2/s); negative of closed-path line integral of v dot ds
  Lambda_src - Source strength, volume flux per unit depth (m^2/s)
  kappa - Doublet strength (m^3/s); kappa = ell * Lambda_src in the limit
  R - Cylinder radius (m); also gas constant in C
  v_r, v_theta - Radial and azimuthal velocity components (m/s)
  ell - Source-to-sink separation distance (m); for Rankine oval
  psi_stag - Stagnation streamline value of psi (m^2/s)

### Airfoils and Thin-Airfoil Theory (Lec H)
  gamma_vort - Vortex strength per unit length along camber line (1/s); gamma_vort = d(Gamma_circ)/ds
  s - Arc length along camber line (m)
  x_0 - Evaluation point along the chord (m)
  theta_thin - Transformed coordinate; x = (c/2)(1 - cos(theta_thin))
  theta_p - Transformed coordinate at point of maximum camber
  m_naca - NACA 4-series maximum camber (fraction of chord)
  p_naca - NACA 4-series position of maximum camber (fraction of chord)
  A_0, A_1, A_2, A_n - Fourier coefficients of vortex distribution (dimensionless)
  c_m_LE - Pitching moment coefficient about leading edge (dimensionless)
  c_m_c4 - Pitching moment coefficient about quarter chord (dimensionless)

### Constants for Air (gamma = 1.4)
  gamma = 1.4
  R = 287 J/(kg*K)
  Cp = 1005 J/(kg*K)
  Cv = 718 J/(kg*K)
  gamma/(gamma-1) = 3.5
  (gamma+1)/(gamma-1) = 6
  2*gamma/(gamma+1) = 7/6 ~ 1.1667
  a_star/a_0 = 0.913
  p_star/p_0 = 0.528
  T_star/T_0 = 0.833
  nu_pm_max (as M -> infinity) = 130.5 degrees
  R_u = 8314 J/(kmol*K)
  M_mol_air ~ 29 kg/kmol

---

## 2. Core Methods & Procedures

### Aircraft Cruise Equilibrium (Lec A)
Steps:
1. Construct a free-body diagram with weight W at the CG, lift L at the wing AC, drag D parallel to flight, thrust T parallel to flight (opposing drag), and tail lift L_t at horizontal-tail AC.
2. Apply vertical force balance: L = W (steady cruise).
3. Apply horizontal force balance: T = D (steady cruise).
4. Apply moment balance about the wing AC: L_t * ell_t = m_w_AC - W*(x_CG - x_w_AC).
5. Compute coefficients: C_L = L/(q_inf * S_ref) and similar.
Key rule: In cruise, the aircraft is in static equilibrium. Tail lift L_t balances the residual moment about the wing AC.

### Computing Lift from Pressure Distribution (Lec A)
Steps:
1. Identify p_top(x) and p_bottom(x) on the airfoil.
2. Compute L_prime = integral from 0 to c of [p_bottom(x) - p_top(x)] dx (per unit span).
3. Or use C_p: c_l = integral from 0 to 1 of [C_p_bottom - C_p_top] d(x/c).
4. The sectional lift coefficient is the area inside the C_p curve.
Key rule: Use gauge pressure or absolute pressure - constants cancel around a closed body.

### Computing Moment from Pressure Distribution (Lec A)
Steps:
1. Choose a MRC (typically c/4).
2. Compute m_prime_MRC = integral from 0 to c of [p_bottom(x) - p_top(x)] * (c/4 - x) dx.
3. Or use C_p: c_m_MRC = integral from 0 to 1 of [C_p_bottom - C_p_top] * (1/4 - x/c) d(x/c).
Key rule: Positive m is nose-up. c_m_c4 is small because lift is concentrated near leading edge (short lever arm).

### Aircraft Drag Buildup (Lec A)
Steps:
1. Compute parasitic drag: C_D_0 = C_f * (S_wet/S_ref) + other.
2. Compute induced drag: C_D_i = C_L^2/(pi * e * AR).
3. Total: C_D = C_D_0 + C_L^2/(pi * e * AR).
4. For best L/D: C_L_best = sqrt(pi * e * AR * C_D_0); (L/D)_max = sqrt(pi*e*AR/(4*C_D_0)).
Key rule: Use Oswald e (combines span efficiency + airfoil C_L^2 viscous drag), not span efficiency alone.

### Control Volume Analysis - Mass Conservation (Lec B - HIGH FINAL PRIORITY)
Steps:
1. Define the control volume explicitly (boundaries 1, 2, 3, 4...).
2. Identify n_hat (outward unit normal) on each boundary.
3. List assumptions: steady (d/dt = 0), incompressible (rho = const), 2D with depth b, streamlines (v dot n_hat = 0), etc.
4. Write: integral over V of d(rho)/dt dV + integral over A of rho*(V_vec dot n_hat) dA = 0.
5. For steady flow: integral over A of rho*(V_vec dot n_hat) dA = 0.
6. Evaluate flux at each boundary. Sign convention: outward flow is positive (V_vec dot n_hat > 0).
7. Solve for unknown geometry (e.g., h_0) or velocity.
Key rule: Boundaries that are streamlines have zero mass flux. The cylinder drag example uses streamlines on top/bottom and integrates u(y) profiles in/out.

### Control Volume Analysis - Momentum Conservation (Lec B)
Steps:
1. Define the control volume and identify n_hat.
2. Write x-momentum: integral d(rho*u)/dt dV + integral rho*u*(V dot n_hat) dA = -integral p*n_hat_x dA + F_x_on_body.
3. Split surfaces: A_prime where pressure is known and viscosity negligible; A_doubleprime where stresses are unknown (i.e., on the body).
4. The unknown F_A_doubleprime usually represents the force the fluid exerts on the body. By Newton's 3rd law, force on the body from fluid is opposite.
5. CRITICAL: rho * u * (V dot n_hat) is NOT rho * (V dot V) * n_hat. They are different.
Key rule: Boundary integrals use the OUTWARD normal. Body force F is what you solve for.

### Reynolds Transport Theorem Application (Lec B)
Steps:
1. Pick a conserved quantity B with per-unit-volume value b.
2. Lagrangian statement: dB_sys/dt = B_dot_ext.
3. Convert to Eulerian: integral d(b)/dt dV + integral b*(V dot n_hat) dA = B_dot_ext.
4. The surface flux term tracks how quickly the conserved quantity leaves the CV.
Key rule: B can be scalar (mass, energy) or vector (momentum); b must match. For mass: B = m, b = rho. For momentum: B = m*V, b = rho*V_vec.

### Differential Form Conversion (Lec B)
Steps:
1. Start from integral form.
2. Apply divergence theorem to convert surface integrals to volume integrals.
3. Combine into a single triple integral.
4. Argue that since equation must hold for any V, integrand is zero pointwise.
5. Result is a PDE.
Key rule: Continuity (B.14): d(rho)/dt + div(rho*V) = 0. Incompressible: div(V) = 0. Euler (B.19): rho * (dV/dt + (V dot grad)V) = -grad(p).

### Bernoulli's Equation Application (Lec B / Lec C)
Steps:
1. Identify the streamline from upstream (or known) point to point of interest.
2. Check assumptions: steady, inviscid, adiabatic, along a streamline. If incompressible too, use simpler form.
3. Incompressible: p + (1/2)*rho*V^2 = constant. Often: p_inf + (1/2)*rho*U_inf^2 = p + (1/2)*rho*V^2.
4. Compressible: (1/2)*V^2 + Cp*T = Cp*T_0 = constant.
Key rule: Bernoulli's equation is just energy conservation + mass conservation along a streamline. It works across some streamlines only if the flow is irrotational.

### Speed of Sound and Mach Number (Lec C)
Steps:
1. Local static temperature T must be known.
2. a = sqrt(gamma * R * T). For air: a = sqrt(1.4 * 287 * T).
3. M = V/a.
4. Both are LOCAL properties - they vary along streamlines.
Key rule: Sound speed depends ONLY on T. The compression in a sound wave is isentropic, not isothermal.

### Stagnation Properties from Static Properties (Lec C)
Steps:
1. Know M and one static property.
2. T_0/T = 1 + ((gamma-1)/2) * M^2. Valid along adiabatic streamlines (even across shocks).
3. p_0/p = [1 + ((gamma-1)/2) * M^2]^(gamma/(gamma-1)). Valid ONLY along ISENTROPIC streamlines.
4. rho_0 from ideal gas: rho_0 = p_0/(R*T_0).
Key rule: T_0 conserved across shocks; p_0 DECREASES across shocks (entropy increases).

### Subsonic Pitot Tube (Lec C)
Steps:
1. Pitot reads p_0; static port reads p_inf; temperature port reads T_0.
2. Compute p_0/p_inf ratio.
3. Solve [1 + 0.2*M_inf^2]^3.5 = p_0/p_inf for M_inf.
4. Find T_inf = T_0 / (1 + 0.2*M_inf^2).
5. a_inf = sqrt(gamma*R*T_inf), V_inf = M_inf * a_inf.
Key rule: For M_inf < 1, no shock. For M_inf > 1, must use Rayleigh Pitot formula (shock forms ahead of probe).

### Normal Shock Property Jumps (Lec D)
Steps:
1. Given upstream M1 > 1.
2. M2^2 = [1 + ((gamma-1)/2)*M1^2] / [gamma*M1^2 - (gamma-1)/2].
3. p2/p1 = 1 + (2*gamma/(gamma+1)) * (M1^2 - 1).
4. rho2/rho1 = (gamma+1)*M1^2 / [(gamma-1)*M1^2 + 2].
5. T2/T1 = (p2/p1) * (rho1/rho2).
6. p0_2/p0_1 found from isentropic relation at M2 and M1, multiplied by p2/p1.
7. Or use normal shock tables for the ratios.
Key rule: M1 > 1 required. M2 < 1 always. T_0 conserved; p_0 drops. NOT isentropic (cannot use p/rho^gamma).

### Oblique Shock Analysis Given M1 and theta (Lec D)
Steps:
1. Compute M1_n = M1 * sin(theta) and M1_t = M1 * cos(theta).
2. Apply normal shock relations to M1_n to get M2_n, p2/p1, rho2/rho1, T2/T1.
3. Compute M2_t = M1_t * (T2/T1)^(-1/2).
4. Compute M2 = sqrt(M2_n^2 + M2_t^2). M2 can be > 1.
5. Compute deflection: delta = theta - arctan(M2_n/M2_t).
6. For p0_2/p0_1: use isentropic relation at full M2 and M1: (p0/p at M1)/(p0/p at M2) inverted; or (p2/p1) * [(1 + 0.2*M2^2)/(1 + 0.2*M1^2)]^3.5.
Key rule: Normal-component direction acts like a normal shock. Tangential velocity w is constant but tangential Mach changes because T changes. Do NOT read p0 ratios from normal shock tables for oblique shocks.

### Oblique Shock Analysis Given M1 and delta (Lec D)
Steps:
1. Use NACA 1135 chart: enter delta on x-axis, intersect M1 curve, read theta from y-axis. Always weak-shock branch (lower theta).
2. Proceed as above.
Key rule: Each M1 has a max delta. Beyond max delta, no attached oblique shock exists - a detached normal/bow shock forms with subsonic flow behind. At delta = 0, theta = mu_mach (Mach wave).

### Prandtl-Meyer Expansion (Lec D - HIGH FINAL PRIORITY)
Steps:
1. Given M1 > 1 and expansion angle alpha_pm.
2. Look up nu_pm(M1) from PM table.
3. Compute nu_pm(M2) = alpha_pm + nu_pm(M1).
4. Look up M2 from PM table inverse.
5. Static properties via isentropic relations (p_0, T_0 conserved across the fan):
   p2/p1 = [(1 + 0.2*M1^2)/(1 + 0.2*M2^2)]^3.5
   T2/T1 = (1 + 0.2*M1^2)/(1 + 0.2*M2^2).
6. Fan geometry: first wave at mu_1 = arcsin(1/M1) above incoming surface; last wave at mu_2 = arcsin(1/M2) above outgoing surface.
Key rule: Expansion is ISENTROPIC. All stagnation properties preserved. M increases, p decreases, T decreases. Max possible expansion from M=1 is nu_pm_max = 130.5 degrees (then M -> infinity, p -> 0).

### Supersonic Flat-Plate Airfoil Lift and Drag (Lec D - HIGHEST FINAL PRIORITY)
This is THE supersonic lift problem.

Setup: Flat plate at angle of attack alpha in supersonic flow M_inf > 1.
- BOTTOM surface: flow turns INTO itself by angle delta = alpha => OBLIQUE SHOCK => p_bot > p_inf.
- TOP surface: flow turns AWAY from itself by angle alpha => PRANDTL-MEYER EXPANSION => p_top < p_inf.

Steps:
1. Bottom: Use NACA 1135 with M_inf and delta = alpha to find theta. Compute M1_n = M_inf*sin(theta). Get p_bot/p_inf = 1 + (2*gamma/(gamma+1))*(M1_n^2 - 1) from D.4.
2. Top: Compute nu_pm(M_inf), then nu_pm(M_top) = alpha + nu_pm(M_inf). Look up M_top. Compute p_top/p_inf = [(1 + 0.2*M_inf^2)/(1 + 0.2*M_top^2)]^3.5.
3. Geometry: L_prime = c*(p_bot - p_top)*cos(alpha); D_prime = c*(p_bot - p_top)*sin(alpha).
4. Coefficients (using q_inf = (gamma/2)*p_inf*M_inf^2):
   c_l = [2*cos(alpha) / (gamma*M_inf^2)] * (p_bot/p_inf - p_top/p_inf)
   c_d = [2*sin(alpha) / (gamma*M_inf^2)] * (p_bot/p_inf - p_top/p_inf)
   c_d = c_l * tan(alpha)  [ALWAYS for a flat plate]
5. Lift slope (Ackeret linear theory): dc_l/dalpha = 4/sqrt(M_inf^2 - 1).
Key rule: Supersonic lift comes from the PRESSURE DIFFERENCE between top (PM-expansion lowered) and bottom (oblique-shock raised). Unlike subsonic flow, the flat plate has NONZERO inviscid drag (wave drag) because the shocks generate entropy. c_d = c_l*tan(alpha) for flat plate.

### Quasi-1D Nozzle Analysis (Lec E)
Steps:
1. Identify reservoir conditions (p_0, T_0) and exit conditions or geometry.
2. Use Mach-area relation: (A/A_star)^2 = (1/M^2) * [(2 + (gamma-1)*M^2)/(gamma+1)]^((gamma+1)/(gamma-1)).
3. Check choking: compute Mach corresponding to p_0/p_exit isentropically. Use that to get tentative A_star = A_exit/(A/A_star ratio). If tentative A_star < A_throat: flow is subsonic everywhere. If tentative A_star > A_throat: flow is choked, actual A_star = A_throat.
4. Choked mass flow: m_dot = rho_star * a_star * A_star.
5. If a shock occurs in the diverging section, A_star changes across it (entropy increases). Use M1, M2 across the shock to find (A_star)_2 / (A_star)_1.
Key rule: For supersonic flow downstream of throat, p_exit must be sufficiently low (less than threshold ~0.094*p_0 for A_exit/A_star = 2). Between thresholds, a shock forms in the diverging section.

### Potential Flow - Velocity Potential and Streamfunction (Lec G)
Steps:
1. For irrotational flow (curl(V) = 0): define phi such that V = grad(phi). u = d(phi)/dx, v = d(phi)/dy.
2. For 2D incompressible flow: define psi such that u = d(psi)/dy and v = -d(psi)/dx.
3. Both satisfy Laplace's equation: grad^2(phi) = 0 and grad^2(psi) = 0 (in 2D incompressible irrotational flow).
4. Lines of constant phi perpendicular to streamlines; lines of constant psi are streamlines.
Key rule: phi exists in 3D when irrotational; psi exists only in 2D incompressible flows (no irrotationality needed). For airfoil work we use both - 2D incompressible irrotational.

### Superposition of Elementary Flows (Lec G - HIGH FINAL PRIORITY)
Steps:
1. Laplace's equation is linear: solutions add.
2. Build up complex flows by adding elementary ones, possibly shifted from origin.
3. Find stagnation points where total velocity vector is zero.
4. Find psi at stagnation points: psi_stag is constant along the stagnation streamline.
5. The stagnation streamline IS the body shape - fluid outside originates from freestream; fluid inside originates from internal sources.
6. To find pressure on the body: compute V on the surface, then Bernoulli: p + (1/2)*rho*V^2 = p_inf + (1/2)*rho*U_inf^2.
7. Integrate pressure to get L_prime and D_prime (or use Kutta-Joukowski if circulation is known).
Elementary flows:
- Uniform: phi = U_inf*x, psi = U_inf*y.
- Source (strength Lambda_src): phi = (Lambda_src/(2*pi))*ln(r), psi = (Lambda_src/(2*pi))*theta. v_r = Lambda_src/(2*pi*r), v_theta = 0.
- Sink: source with negative Lambda_src.
- Vortex (strength Gamma_circ): phi = -(Gamma_circ/(2*pi))*theta, psi = (Gamma_circ/(2*pi))*ln(r). v_theta = -Gamma_circ/(2*pi*r), v_r = 0.
- Doublet (strength kappa): phi = (kappa/(2*pi))*cos(theta)/r, psi = -(kappa/(2*pi))*sin(theta)/r.

Composite shapes:
- Uniform + Source = Rankine Half Body (open in back).
- Uniform + Source + Sink (equal strength, separated by ell) = Rankine Oval (closed).
- Uniform + Doublet = Flow over a Cylinder of radius R, where kappa = 2*pi*U_inf*R^2.
- Uniform + Doublet + Vortex = Lifting Cylinder. Generates lift L_prime = rho*U_inf*Gamma_circ.

Key rule: For lift, you MUST add circulation. Sources and sinks alone produce zero net force (d'Alembert's paradox). VORTEX STRENGTH IS WHERE LIFT COMES FROM SUBSONICALLY.

### Kutta-Joukowski Theorem (Lec G - HIGHEST FINAL PRIORITY)
Steps:
1. Identify Gamma_circ (total circulation around the body).
2. L_prime = rho * U_inf * Gamma_circ.
3. Gamma_circ is defined as the negative of the closed-path line integral of V dot ds counterclockwise around the body: Gamma_circ = -closed_loop(V dot ds).
4. For multiple vortices inside the body: Gamma_circ = sum of vortex strengths.
5. By Stokes theorem: Gamma_circ = -double_integral(curl(V) dA) over enclosed surface.
Key rule: This is the principal way to compute 2D lift. THE WHOLE POINT of subsonic aerodynamics is finding Gamma_circ for a given shape and freestream.

### Thin Airfoil Theory - Symmetric Airfoils (Lec H)
Steps:
1. Distribute vortices along the camber line (which is the chord line for symmetric airfoils).
2. Coordinate transform: x = (c/2)*(1 - cos(theta_thin)).
3. Vortex strength: gamma_vort(theta_thin) = 2*alpha*U_inf*(1 + cos(theta_thin))/sin(theta_thin).
4. Verify Kutta condition: gamma_vort(theta_thin = pi) = 0. Check.
5. Lift: L_prime = rho*U_inf*integral from 0 to c of gamma_vort(x) dx = pi*rho*U_inf^2*c*alpha.
6. c_l = 2*pi*alpha (alpha in radians).
7. Moment about LE: c_m_LE = -(pi*alpha)/2.
8. Moment about c/4: c_m_c4 = 0.
Key rule: For a symmetric thin airfoil, c/4 is BOTH the aerodynamic center AND the center of pressure. c_l_alpha = 2*pi per radian.

### Thin Airfoil Theory - Cambered Airfoils (Lec H)
Steps:
1. Use Fourier sine series for gamma_vort:
   gamma_vort(theta_thin) = 2*U_inf*[A_0*(1 + cos(theta_thin))/sin(theta_thin) + sum_n(A_n * sin(n*theta_thin))].
2. Compute Fourier coefficients:
   A_0 = alpha - (1/pi)*integral from 0 to pi of (dz/dx) d(theta_thin).
   A_n = (2/pi)*integral from 0 to pi of (dz/dx)*cos(n*theta_thin) d(theta_thin).
3. Only A_0, A_1, A_2 needed for lift and moment.
4. CRITICAL: Take dz/dx (derivative with respect to x) first, THEN substitute x = (c/2)(1 - cos(theta_thin)) to express as function of theta_thin.
5. Lift coefficient: c_l = 2*pi*A_0 + pi*A_1 = 2*pi*alpha + 2*[A_1*pi - integral term].
6. Zero-lift angle: alpha_L0 = -(1/pi)*integral from 0 to pi of (dz/dx)*(cos(theta_thin) - 1) d(theta_thin), or solve c_l = 0.
7. Moment about LE: c_m_LE = -(pi/2)*(A_0 + A_1 - A_2/2).
8. Moment about c/4: c_m_c4 = (pi/4)*(A_2 - A_1). Not a function of alpha => c/4 is the aerodynamic center.
Key rule: Lift slope is still 2*pi per radian (camber only shifts the lift curve, doesn't change its slope). The c_m_c4 is non-zero but constant in alpha, making c/4 the AC. For a piecewise-linear camber with hinge at (x_p, z_p) = (p*c, m*c), compute integrals piece by piece.

### NACA 4-Series Airfoil Analysis (Lec H)
Steps:
1. Decode designation (e.g., 2412): m_naca = 2% = 0.02, p_naca = 4/10 = 0.40, thickness = 12% (ignored in thin-airfoil theory).
2. Camber line: z = m_naca*(2*p_naca*x - x^2)/p_naca^2 for x < p_naca; z = m_naca*[(1 - 2*p_naca) + 2*p_naca*x - x^2]/(1 - p_naca)^2 for x > p_naca.
3. Camber slopes:
   For x < p_naca: dz/dx = (m_naca/p_naca^2)*(cos(theta_thin) + 2*p_naca - 1) - after substitution.
   For x > p_naca: dz/dx = (m_naca/(1-p_naca)^2)*(cos(theta_thin) + 2*p_naca - 1).
4. Find theta_p: cos(theta_p) = 1 - 2*p_naca.
5. Integrate piecewise (fore from 0 to theta_p, aft from theta_p to pi) to get A_0, A_1, A_2.
6. Get c_l, c_m_c4, alpha_L0.
Key rule: The slope (cos(theta_thin) + 2*p_naca - 1) is the same functional form on both sides; only the prefactor changes at theta_p.

---

## 3. Formulas & Equations

### Lec A: Aircraft and Aerodynamic Coefficients
  Dynamic pressure: q_inf = (1/2)*rho_inf*U_inf^2
  Compressible q_inf: q_inf = (gamma/2)*p_inf*M_inf^2
  Stagnation pressure (low M): p_0 = p_inf + (1/2)*rho_inf*U_inf^2
  3D Lift: L = q_inf * S_ref * C_L  =>  C_L = L/(q_inf*S_ref)
  3D Drag: D = q_inf * S_ref * C_D  =>  C_D = D/(q_inf*S_ref)
  3D Moment: m = q_inf*S_ref*c_bar*C_m  =>  C_m = m/(q_inf*S_ref*c_bar)
  2D Sectional lift: L_prime = q_inf * c * c_l
  2D Sectional drag: D_prime = q_inf * c * c_d
  2D Sectional moment: m_prime = q_inf * c^2 * c_m
  Pressure coefficient: C_p = (p - p_inf)/q_inf
  Sectional lift from C_p: c_l = integral from 0 to 1 of [C_p_bot(x/c) - C_p_top(x/c)] d(x/c)
  Sectional moment from C_p: c_m = integral from 0 to 1 of [C_p_bot - C_p_top]*(1/4 - x/c) d(x/c)
  Thin-airfoil theory baseline: c_l = 2*pi*(alpha - alpha_L0) (alpha in radians)
  Aspect ratio: AR = b^2/S_ref. Rectangular: AR = b/c.
  Mean aerodynamic chord: c_bar = (1/S_ref) * integral over b of [c(y)]^2 dy
  Induced drag: C_D_i = C_L^2/(pi*e*AR)
  Simple drag model: C_D = C_D_0 + C_L^2/(pi*e*AR)
  Parasitic drag: C_D_0 = C_f*(S_wet/S_ref) + other
  Best lift coefficient: C_L_best = sqrt(pi*e*AR*C_D_0)
  Best L/D: (L/D)_max = sqrt(pi*e*AR/(4*C_D_0))
  Stall speed: V_stall = sqrt(2*W/(rho*C_L_max*S_ref))
  High-lift increment: Delta_C_L_max = 0.9 * Delta_C_L_device * (S_flapped/S_ref) * cos(Lambda_hinge)
  Body-to-wind rotation (beta=0): A = D*cos(alpha) - L*sin(alpha); N = L*cos(alpha) + D*sin(alpha)

Aerodynamic angles:
  alpha = arctan(w_b/u_b)
  beta = arctan(-v_b/sqrt(u_b^2 + w_b^2))
  alpha_t = arctan(sqrt(v_b^2 + w_b^2)/u_b)
  phi = arctan(v_b/w_b)

### Lec B: Conservation Equations
Reynolds number: Re_c = rho*U_inf*c/mu_visc
Froude number squared: Fr^2 = U_inf^2/(g*h)
Mach number squared: M_inf^2 = U_inf^2/a_inf^2

Mass conservation (integral): integral_V d(rho)/dt dV + integral_A rho*(V_vec dot n_hat) dA = 0
Mass conservation (differential): d(rho)/dt + div(rho*V_vec) = 0
Incompressible: div(V_vec) = 0  or  du/dx + dv/dy + dw/dz = 0

Momentum conservation (integral): integral_V d(rho*V_vec)/dt dV + integral_A rho*V_vec*(V_vec dot n_hat) dA = -integral_A_prime p*n_hat dA + F_A_doubleprime
Euler equation (vector): rho * [d(V_vec)/dt + (V_vec dot grad)V_vec] = -grad(p)
Euler x-component: rho*[du/dt + u*du/dx + v*du/dy + w*du/dz] = -dp/dx

Material derivative: D(q)/Dt = d(q)/dt + (V_vec dot grad)q = d(q)/dt + u*dq/dx + v*dq/dy + w*dq/dz

Energy conservation (integral): integral_V d(rho*E)/dt dV + integral_S (rho*E + p)*(V_vec dot n_hat) dA = 0 (adiabatic, inviscid)
Where E = (1/2)*V^2 + e
Differential: rho*[de/dt + V_vec dot grad(e)] = -p*div(V_vec)
Or: rho*Cv*[dT/dt + V_vec dot grad(T)] = -p*div(V_vec)

Bernoulli (compressible, along streamline): (1/2)*V^2 + Cp*T = constant = (1/2)*V_in^2 + Cp*T_in
Bernoulli (incompressible, along streamline): (1/2)*rho*V^2 + p = constant

Streamline equations (2D): dy/dx = v/u  or  u*dy - v*dx = 0
3D: V_vec cross ds = 0

Divergence Theorem: integral_V div(q_vec) dV = integral_A q_vec dot n_hat dA
Fundamental Theorem (gradient form): integral_V grad(q) dV = integral_A q*n_hat dA

### Lec C: Ideal-Gas Thermodynamics
(C.1) Ideal gas law: p = rho * R * T
(C.2) R = R_u / M_mol
(C.3) Internal energy: e(T) = Cv*T + e_ref
(C.4) Enthalpy: h(T) = Cp*T + h_ref
(C.5) Cp = Cv + R
(C.6) gamma = Cp/Cv
(C.7) Entropy: ds = Cv*(dT/T) - R*(d(rho)/rho)
(C.8) Isentropic relation derivation: Cv*dT/T = R*d(rho)/rho
(C.9) Isentropic state: p/rho^gamma = constant  or  p2/p1 = (rho2/rho1)^gamma
Adiabatic lapse rate: p/p_0 = [1 - ((gamma-1)/gamma)*(g*z/(R*T_0))]^(gamma/(gamma-1))
(C.10) Speed of sound: a = sqrt(gamma*R*T)
(C.11) Mach number: M = V/a = V/sqrt(gamma*R*T)
Compressible Bernoulli: (1/2)*V^2 + Cp*T = Cp*T_0
(C.12) Stagnation temperature: T_0/T = 1 + ((gamma-1)/2)*M^2
(C.13) Stagnation pressure: p_0/p = [1 + ((gamma-1)/2)*M^2]^(gamma/(gamma-1))
Stagnation density: rho_0/rho = [1 + ((gamma-1)/2)*M^2]^(1/(gamma-1))
(C.14) Stagnation sound speed: a_0/a = [1 + ((gamma-1)/2)*M^2]^(1/2)
(C.15) Critical sound speed ratio: a_star/a_0 = [2/(gamma+1)]^(1/2) ~ 0.913 for gamma=1.4

### Lec D: Supersonic Flow
Mach angle:
(D.1) mu_mach = arcsin(1/M)

Normal Shock (M1 > 1):
(D.2) a_star^2 = V1 * V2  (Prandtl's relation; a_star constant across shock)
(D.3) M2^2 = [1 + ((gamma-1)/2)*M1^2] / [gamma*M1^2 - (gamma-1)/2]
(D.4) p2/p1 = 1 + (2*gamma/(gamma+1))*(M1^2 - 1)
(D.5) rho2/rho1 = (gamma+1)*M1^2 / [(gamma-1)*M1^2 + 2]
(D.6) T2/T1 = (p2/p1) * (rho1/rho2)
T0 conserved across normal shock; p0 decreases.

Oblique Shock:
(D.7) M1_n = M1 * sin(theta)
M1_t = M1 * cos(theta)
Use M1_n in Eqns D.3-D.6 to get M2_n, p2/p1, T2/T1, rho2/rho1
(D.8) M2_t = M1_t * (T2/T1)^(-1/2)  [tangential VELOCITY w1=w2 but tangential MACH changes]
Or: M2_t = M1*cos(theta) * (T2/T1)^(-1/2)
(D.9) M2^2 = M2_n^2 + M2_t^2
(D.10) delta = theta - arctan(M2_n / M2_t)
Stagnation pressure ratio (compute from full Mach numbers):
  p0_2/p0_1 = (p2/p1) * [(1 + ((gamma-1)/2)*M2^2)/(1 + ((gamma-1)/2)*M1^2)]^(gamma/(gamma-1))

Prandtl-Meyer Expansion:
(D.11) d(alpha_pm) = sqrt(M^2 - 1) / [M*(1 + ((gamma-1)/2)*M^2)] dM
(D.12) alpha_pm = integral from M1 to M2 of d(alpha_pm)
(D.13) alpha_pm = nu_pm(M2) - nu_pm(M1)
(D.14) nu_pm(M2) = alpha_pm + nu_pm(M1)
nu_pm exact form: nu_pm(M) = sqrt((gamma+1)/(gamma-1))*arctan(sqrt(((gamma-1)/(gamma+1))*(M^2-1))) - arctan(sqrt(M^2-1))
nu_pm_max (as M -> infinity) = 130.5 degrees for gamma=1.4
Isentropic expansion - all stagnation properties preserved.
Static p ratio: p2/p1 = [(1 + 0.2*M1^2)/(1 + 0.2*M2^2)]^3.5

Supersonic Flat-Plate Airfoil:
L_prime = c*(p_bot - p_top)*cos(alpha)
D_prime = c*(p_bot - p_top)*sin(alpha)
c_l = [2*cos(alpha) / (gamma*M_inf^2)] * (p_bot/p_inf - p_top/p_inf)
c_d = [2*sin(alpha) / (gamma*M_inf^2)] * (p_bot/p_inf - p_top/p_inf)
c_d = c_l * tan(alpha)  [FLAT PLATE ONLY]
Lift slope (Ackeret): dc_l/d(alpha) = 4/sqrt(M_inf^2 - 1)
c_l Ackeret: c_l = 4*alpha/sqrt(M_inf^2 - 1)  [linearized, small alpha]

### Lec E: Quasi-1D Nozzles
Area-velocity relation: dA/A = (M^2 - 1)*dV/V
(E.1) (A/A_star)^2 = (1/M^2) * [(2 + (gamma-1)*M^2)/(gamma+1)]^((gamma+1)/(gamma-1))
At M=1: p_star/p_0 = 0.528, T_star/T_0 = 0.833, rho_star/rho_0 ~ 0.634 (for gamma=1.4)
For choked Aexit/Astar=2: pexit/p0 < 0.094 (fully supersonic), 0.094 < pexit/p0 < 0.515 (shock in diverging section), 0.515 < pexit/p0 < 0.937 (subsonic but choked at throat), pexit/p0 > 0.937 (subsonic throughout).
Choked mass flow: m_dot = rho_star * a_star * A_star, where rho_star = p_star/(R*T_star)

### Lec G: Potential Flow
Vorticity (3D): omega_vec = curl(V_vec)
2D vorticity: omega = dv/dx - du/dy
Rotation rate: Omega = (1/2)*omega
Crocco's theorem: D(omega)/Dt = 0 in inviscid flow (vorticity conserved along streamlines)
Implication: For irrotational upstream flow (uniform), the entire flow is irrotational (omega = 0 everywhere).

Velocity potential (irrotational flow): V_vec = grad(phi)
  u = d(phi)/dx, v = d(phi)/dy, w = d(phi)/dz
Streamfunction (2D incompressible flow):
  u = d(psi)/dy, v = -d(psi)/dx
Polar/cylindrical:
  (v_r, v_theta, v_z) = (d(phi)/dr, (1/r)*d(phi)/d(theta), d(phi)/dz)
  (v_r, v_theta) = ((1/r)*d(psi)/d(theta), -d(psi)/dr)  [2D]
  div(V) in cylindrical: (1/r)*d(r*v_r)/dr + (1/r)*d(v_theta)/d(theta) + dv_z/dz
  omega_z = (1/r)*d(r*v_theta)/dr - (1/r)*d(v_r)/d(theta)

Laplace's equation: grad^2(phi) = 0 (also grad^2(psi) = 0 in 2D)
  In Cartesian 2D: d^2(phi)/dx^2 + d^2(phi)/dy^2 = 0

Elementary 2D Flow Solutions:
Uniform flow (speed U_inf, x-direction):
  u = U_inf, v = 0
  phi = U_inf*x
  psi = U_inf*y

Source flow (volume flux Lambda_src):
  v_r = Lambda_src/(2*pi*r), v_theta = 0
  phi = (Lambda_src/(2*pi))*ln(r)
  psi = (Lambda_src/(2*pi))*theta

Sink flow: source with negative Lambda_src.

2D Vortex (strength Gamma_circ):
  v_r = 0, v_theta = -Gamma_circ/(2*pi*r)  [NOTE THE MINUS SIGN]
  phi = -(Gamma_circ/(2*pi))*theta
  psi = (Gamma_circ/(2*pi))*ln(r)

Doublet (strength kappa):
  phi = (kappa*cos(theta))/(2*pi*r)
  psi = -(kappa*sin(theta))/(2*pi*r)
  v_r = -(kappa/(2*pi*r^2))*cos(theta)
  v_theta = -(kappa/(2*pi*r^2))*sin(theta)

Composite Bodies (superposition):
Uniform + Source = Rankine Half Body:
  Stagnation point: (r, theta) = (Lambda_src/(2*pi*U_inf), pi)
  psi_stag = Lambda_src/2
  Body shape: r = (Lambda_src/(2*pi*U_inf)) * (pi - theta)/sin(theta)

Uniform + Source + Sink (separated by ell) = Rankine Oval:
  Stagnation points at: x = +/- (ell/2)*sqrt(1 + Lambda_src/(pi*U_inf*ell)), y = 0
  psi_stag = 0

Uniform + Doublet (kappa = 2*pi*U_inf*R^2) = Cylinder of radius R:
  psi = U_inf*r*(1 - R^2/r^2)*sin(theta)
  phi = U_inf*r*(1 + R^2/r^2)*cos(theta)
  Surface velocity: v_theta(R, theta) = -2*U_inf*sin(theta)
  Surface pressure coefficient: C_p(theta) = 1 - 4*sin^2(theta)
  Net lift = 0, net drag = 0 (d'Alembert's paradox)

Uniform + Doublet + Vortex (at origin) = Lifting Cylinder:
  psi = U_inf*r*(1 - R^2/r^2)*sin(theta) + (Gamma_circ/(2*pi))*ln(r)
  C_p(R, theta) = 1 - 4*sin^2(theta) - 2*Gamma_circ*sin(theta)/(pi*U_inf*R) - (Gamma_circ/(2*pi*U_inf*R))^2
  c_l = Gamma_circ/(U_inf*R)
  L_prime = rho*U_inf*Gamma_circ
  c_d = 0 (d'Alembert again!)
  Stagnation point on cylinder surface (when |Gamma_circ| < 4*pi*U_inf*R):
    theta_stag = arcsin(-Gamma_circ/(4*pi*U_inf*R))

Kutta-Joukowski Theorem (general 2D bodies):
(G.19) L_prime = rho*U_inf*Gamma_circ
Circulation (definition):
(G.21) Gamma_circ = -closed_loop(V_vec dot ds_vec)  [counterclockwise path]
Stokes theorem: Gamma_circ = -double_integral_over_A(curl(V_vec) dA)

### Lec H: Thin-Airfoil Theory
Coordinate transformation: x = (c/2)*(1 - cos(theta_thin))
  dx = (c/2)*sin(theta_thin)*d(theta_thin)
  Maps x in [0, c] to theta_thin in [0, pi]

Fundamental Equation of Thin-Airfoil Theory:
(H.3) (1/(2*pi))*integral from 0 to c of gamma_vort(x)/(x_0 - x) dx = U_inf*[alpha - (dz/dx) at x_0]

Total lift (from Kutta-Joukowski):
(H.1) L_prime = rho*U_inf*integral from 0 to c of gamma_vort(s) ds

Glauert's Integral:
(H.6) integral from 0 to pi of cos(n*theta)/[cos(theta) - cos(theta_0)] d(theta) = pi*sin(n*theta_0)/sin(theta_0)

Symmetric Thin Airfoils (z(x) = 0):
(H.5) gamma_vort(theta_thin) = 2*alpha*U_inf*(1 + cos(theta_thin))/sin(theta_thin)
(H.7) c_l = 2*pi*alpha  (alpha in radians)
(H.8) c_m_LE = -(pi*alpha)/2
(H.9) c_m_MRC = pi*alpha^2 form... or more simply
c_m_c4 = 0 for symmetric thin airfoils
=> c/4 is the aerodynamic center AND the center of pressure for symmetric airfoils.

Cambered Thin Airfoils (Fourier sine series):
(H.10) gamma_vort(theta_thin) = 2*U_inf*[A_0*(1 + cos(theta_thin))/sin(theta_thin) + sum_{n=1 to inf} A_n*sin(n*theta_thin)]
(H.11) A_0 = alpha - (1/pi)*integral from 0 to pi of (dz/dx) d(theta_thin)
(H.12) A_n = (2/pi)*integral from 0 to pi of (dz/dx)*cos(n*theta_thin) d(theta_thin)
(H.13) c_l = 2*pi*A_0 + pi*A_1
(H.14) c_m_LE = -(pi/2)*(A_0 + A_1 - A_2/2)
(H.15) c_m_c4 = (pi/4)*(A_2 - A_1)

Zero-lift angle of attack (set c_l = 0):
  alpha_L0 = (1/pi)*integral from 0 to pi of (dz/dx)*(cos(theta_thin) - 1) d(theta_thin)
  Note: For positive camber, alpha_L0 is negative.

c_l in terms of alpha_L0: c_l = 2*pi*(alpha - alpha_L0)

NACA 4-Series (digits "MPXX": M = max camber %, P = max camber position in tenths, XX = thickness %):
  z(x) = m_naca*(2*p_naca*x - x^2)/p_naca^2  for x < p_naca
  z(x) = m_naca*[(1 - 2*p_naca) + 2*p_naca*x - x^2]/(1 - p_naca)^2  for x >= p_naca
With x, p_naca, m_naca all in fractions of c.

dz/dx (after substitution x = (c/2)*(1 - cos(theta_thin))):
  For x < p_naca: dz/dx = (m_naca/p_naca^2)*(cos(theta_thin) + 2*p_naca - 1)
  For x > p_naca: dz/dx = (m_naca/(1 - p_naca)^2)*(cos(theta_thin) + 2*p_naca - 1)
Hinge angle: cos(theta_p) = 1 - 2*p_naca

Kutta Condition Statement: At the trailing edge, V_top = V_bottom (smooth flow departure).
In thin-airfoil theory: gamma_vort(x = c) = 0, i.e., gamma_vort(theta_thin = pi) = 0.

Useful Integrals & Identities:
  integral cos^2(theta) d(theta) = theta/2 + sin(2*theta)/4
  integral cos(theta)*cos(2*theta) d(theta) = sin(theta)/2 + sin(3*theta)/6
  sin(2*theta) = 2*sin(theta)*cos(theta)
  sin(3*theta) = 3*sin(theta) - 4*sin^3(theta)
  cos^2(theta) = (1 + cos(2*theta))/2
  cos(theta)*cos(2*theta) = [cos(theta) + cos(3*theta)]/2
  Antiderivative of (cos(theta) + k): sin(theta) + k*theta

---

## 4. Standard Assumptions & Idealizations

Default assumptions Prof. White applies unless the problem states otherwise:

- Air properties: gamma = 1.4, R = 287 J/(kg*K). Use these unless told otherwise.
- Steady flow: d/dt of all field quantities = 0.
- Inviscid (mu_visc = 0) UNLESS the problem is about drag, boundary layers, or shocks. This means no viscous shear stress in the flow except at viscous boundaries (which are treated separately).
- Adiabatic: no heat transfer (delta_q = 0) unless an engine adds Q_dot explicitly.
- High Reynolds number (Re_c >> 1) => viscous effects can be ignored over most of the flow.
- High Froude number (Fr^2 >> 1) => gravity neglected. (Aircraft Fr ~ 50-100; Fr^2 even larger.)
- Continuum assumption: fluid is a smooth continuous medium, not discrete molecules.
- 2D flow when discussing airfoils (no spanwise variations, w = 0).
- Incompressible flow when M_inf <= 0.3. Density is constant.
- Compressible flow when M_inf > 0.3 (use isentropic relations; thermodynamic state matters).
- Streamlines as control volume boundaries imply (V_vec dot n_hat) = 0 (no mass flux).
- Body surfaces are streamlines (no-penetration condition).
- No-slip is dropped when viscosity is ignored.
- Across normal shocks: NOT isentropic. T_0 conserved; p_0, rho_0 decrease.
- Across oblique shocks: NOT isentropic. T_0 conserved; p_0 decreases (less than normal shock).
- Across Prandtl-Meyer expansion fans: ISENTROPIC. All stagnation properties preserved.
- For thin-airfoil theory: t_max/c << 1, z_max/c << 1, alpha small (cos(alpha) ~ 1, sin(alpha) ~ alpha).
- For supersonic flat plate: shocks are weak enough that the weak-shock branch of NACA 1135 applies.
- Kutta condition is enforced: flow leaves trailing edge smoothly; gamma_vort(c) = 0 in thin-airfoil theory.
- Always use the WEAK SHOCK branch on the NACA 1135 chart (lower theta for given delta).
- Bernoulli's equation (any form) applies ALONG a streamline; applies between streamlines only if flow is irrotational.
- Sign convention: positive lift is up, positive drag is downstream, positive pitch moment is nose-up (+y axis, out the right wing).
- Body-fixed coordinates: x forward (or backward, debated), y out right wing, z up (or down).
- Wind-fixed: x in U_inf direction (downstream), y as in body, z perpendicular to x in the buttline plane.
- Outward unit normal n_hat used in all surface integrals.

---

## 5. Common Problem Archetypes

### Cruise Equilibrium / Find Required Wing Area
Given weight, altitude, cruise Mach, target C_L. Compute q_inf = (gamma/2)*p_inf*M_inf^2 (or (1/2)*rho*V^2). Solve S_ref = W/(q_inf*C_L). Apply moment balance for tail loads if asked.

### Pressure Distribution to Coefficients
Given C_p_top(x) and C_p_bot(x) along an airfoil, integrate from 0 to 1 in x/c to find c_l (subtract top from bottom, integrate) and c_m (multiply by (1/4 - x/c) before integrating). c_l is the area inside the C_p curve.

### Drag Polar / Best L/D
Given AR, e, C_D_0 (or C_f and S_wet/S_ref), use C_D = C_D_0 + C_L^2/(pi*e*AR). Compute C_L_best = sqrt(pi*e*AR*C_D_0) and (L/D)_max = sqrt(pi*e*AR/(4*C_D_0)). At max L/D, induced drag equals parasitic drag.

### Control Volume Mass Conservation (HIGH FINAL PRIORITY)
Given a CV with specified inflow/outflow profiles and boundaries-as-streamlines, write continuity in integral form, apply steady-state simplification, and solve for unknown velocity profile or height. CRITICAL ARCHETYPE - the cylinder-drag and airfoil examples in Lec B use this exact framework. List ALL assumptions explicitly. Boundaries 2 and 4 are typically streamlines (mass flux = 0). Sum of mass flux on inflow (boundary 1) equals sum on outflow (boundary 3).

### Control Volume Momentum (Find Force on Body)
Same setup as mass CV, but now compute momentum flux: rho*u*(V_vec dot n_hat) on each boundary. Total = -integral p*n_hat - F_drag_on_body. CRITICAL: rho*u*(V dot n_hat), NOT rho*V*(V dot V). Pressure assumed p_inf on all CV boundaries unless stated.

### Water Jet on Surface (Momentum Practice)
Steady jet of velocity V_in impinges at angle theta on a flat plate; splits into outgoing flow V_out at angle phi. Apply momentum in x and y to find force R the water exerts on plate. Mass conservation determines mass split.

### Isentropic Flow Stagnation Properties
Given M and (T, p), compute T_0, p_0, rho_0 using C.12 and C.13. Or given p_0 and p with isentropic flow, solve for M. Or use isentropic flow tables.

### Pitot Tube (Subsonic Compressible)
Given p_0, p_inf, T_0 (subsonic), use p_0/p_inf = (1 + 0.2*M_inf^2)^3.5 to solve for M_inf, then T_inf = T_0/(1 + 0.2*M_inf^2), a_inf = sqrt(gamma*R*T_inf), V_inf = M_inf*a_inf.

### Pitot Tube (Supersonic)
Bow shock forms ahead of probe; tip reads p_0_2 (downstream of shock), NOT p_0_1. Workflow: assume M_1, compute p_0_1, then compute jump through shock to get p_0_2/p_inf, iterate to match measured pitot/static ratio.

### Sound Speed and Mach Number
Given V and T, compute a = sqrt(gamma*R*T) and M = V/a. Identify regime: incompressible (M < 0.3), subsonic, transonic (0.7 < M < 1), supersonic (M > 1), hypersonic (M > 6).

### Adiabatic Lapse Rate
Use p/p_0 = [1 - ((gamma-1)/gamma)*(g*z/(R*T_0))]^(gamma/(gamma-1)) up to ~11 km. Valid for isentropic mixing of the lower atmosphere.

### Normal Shock in Engine Inlet
Given M_inf > 1 ahead of inlet, normal shock between stations 1 and 2 (just ahead and behind shock), isentropic deceleration from station 2 to stagnation point at station 3. Use normal shock relations for the jump; isentropic deceleration from 2 to 3. T_0 conserved throughout; p_0 drops only at the shock.

### Oblique Shock Property Jumps
Given M1 and either theta or delta. If delta given, use NACA 1135 chart to find theta. Compute M1_n, apply normal-shock relations, then M2_t and M2. Find p2/p1, T2/T1, rho2/rho1, p0_2/p0_1.

### Oblique Shock Reflection (Inlet Compression)
Series of oblique shocks followed by terminating normal shock - more efficient than one normal shock. After each oblique shock, theta_next is LARGER for same delta because M_local is lower. Used in SR-71, Concorde inlets.

### Prandtl-Meyer Expansion
Given M1 > 1 and expansion angle alpha_pm. Look up nu_pm(M1), add alpha_pm, look up M2. Compute p2/p1 and T2/T1 isentropically. Or solve inversely: given p2/p1, find M2 first then alpha_pm.

### Supersonic Flat-Plate Lift and Drag (HIGHEST FINAL PRIORITY)
THE supersonic lift problem. Flat plate at alpha in M_inf flow. Bottom: oblique shock (compression). Top: PM expansion. Find p_bot/p_inf and p_top/p_inf using both methods. Then c_l, c_d, and verify c_d = c_l*tan(alpha). Compare to Ackeret: c_l_Ackeret = 4*alpha/sqrt(M_inf^2 - 1).

### Nozzle Flow / Choking
Given p_0, p_exit, A_throat, A_exit. Compute tentative M_exit from p_0/p_exit (isentropic). Compute tentative A_star. Compare to A_throat. If A_throat < tentative A_star: not choked; subsonic everywhere. If A_throat > tentative A_star: choked; A_star = A_throat, supersonic downstream of throat (or shock in diverging section depending on p_exit).

### Shock in Diverging Nozzle
For Aexit/A_star=2 example: if 0.094 < p_exit/p_0 < 0.515, shock forms in diverging section. Find shock location: A_star changes across the shock (rho_0 and p_0 decrease, A_star_2/A_star_1 = p_0_1/p_0_2). Iterate or solve directly using the area ratio for the post-shock subsonic flow.

### Elementary Potential Flow Velocity/Streamline (HIGH FINAL PRIORITY)
Given a velocity vector field or phi/psi expression, compute velocities using gradient definitions. Sketch streamlines. Find stagnation points by setting V = 0. Apply Bernoulli to find pressure.

### Superposition - Build a Body Shape (HIGH FINAL PRIORITY - Superimposed Sources/Sinks)
Combine uniform flow + sources + sinks + vortices + doublets to make a body shape. Identify stagnation points (where total V = 0). Find psi_stag. Express body shape as the equation r(theta) or y(x) corresponding to psi = psi_stag. Examples: Rankine half-body, Rankine oval, cylinder, lifting cylinder. SOURCE/SINK PAIRS PRODUCE CLOSED OVALS. Adding VORTEX gives lift.

### Cylinder Flow with Circulation (HIGH FINAL PRIORITY - Vortex Strength is Lift)
Uniform + Doublet + Vortex. Compute v_theta on cylinder surface. Apply Bernoulli to get C_p(theta). Integrate to get c_l = Gamma_circ/(U_inf*R) and c_d = 0. THIS DEMONSTRATES THE KEY POINT: LIFT IS PROPORTIONAL TO VORTEX STRENGTH (CIRCULATION).

### Kutta-Joukowski Application (HIGHEST FINAL PRIORITY - Where Subsonic Lift Comes From)
Given a body with known circulation Gamma_circ, compute L_prime = rho*U_inf*Gamma_circ instantly. For complicated shapes (airfoils with vortex sheets), Gamma_circ = sum of all vortex strengths inside the body. THIS IS THE PRINCIPAL METHOD FOR SUBSONIC LIFT CALCULATION.

### Thin Symmetric Airfoil
Given alpha, immediately write c_l = 2*pi*alpha, c_m_c4 = 0, c_m_LE = -pi*alpha/2. The AC and CP are both at c/4. Lift slope is 2*pi per radian.

### Thin Cambered Airfoil (NACA 4-Series or Piecewise Linear)
1. Express z(x) and compute dz/dx as function of x.
2. Transform: x = (c/2)(1 - cos(theta_thin)). Find theta_p from cos(theta_p) = 1 - 2*p_naca.
3. Compute A_0 = alpha - (1/pi)*integral of (dz/dx) d(theta_thin) [piecewise from 0 to theta_p and theta_p to pi].
4. Compute A_1 = (2/pi)*integral of (dz/dx)*cos(theta_thin) d(theta_thin).
5. Compute A_2 = (2/pi)*integral of (dz/dx)*cos(2*theta_thin) d(theta_thin).
6. Results: c_l = 2*pi*A_0 + pi*A_1 = 2*pi*(alpha - alpha_L0). c_m_c4 = (pi/4)*(A_2 - A_1). alpha_L0 from setting c_l = 0.

### Kutta Condition Statement
Conceptual question: explain why nature selects unique Gamma_circ at a sharp trailing edge. Answer: in inviscid theory, infinite menu of Gamma values is possible; viscosity (boundary layer) prevents infinite velocity at the sharp TE; only one Gamma allows smooth departure. Mathematically: gamma_vort(c) = 0.

### Starting Vortex
Conceptual question: how is circulation generated if Domega/Dt = 0 in inviscid flow? Answer: D omega / Dt = 0 fails at the trailing edge (viscous region). Starting vortex of strength -Gamma_circ is shed into the wake during initial acceleration. Bound vortex on wing has +Gamma_circ. Total circulation around a large CV containing both is zero.

### Aerodynamic Center vs Center of Pressure
AC is the point about which dm/d(alpha) = 0 (moment doesn't change with alpha). CP is the point about which moment is exactly zero. For symmetric thin airfoil, c/4 is both AC and CP. For cambered thin airfoil, c/4 is the AC but the CP moves with alpha.

### Sketch c_l vs alpha
Thin-airfoil theory predicts c_l = 2*pi*(alpha - alpha_L0): linear with slope 2*pi per radian, intercept at alpha_L0 (negative for positive camber). Real airfoils deviate at high alpha (stall: c_l_max around 1.0-1.3 for clean airfoil) and have slightly lower slope due to thickness. Below stall: theory and experiment agree within a few percent. Above stall: c_l drops sharply.

---

## End of Reference
