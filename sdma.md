# MECH 3340 (System Dynamics Modeling and Analysis) — Course Reference

Course: MECH 3340, UT-Dallas, Spring 2026, Prof. Yaoyu Li
Textbook: Palm, "System Dynamics"
NOTE ON EMPHASIS: Exam 3 covers Lectures 10-13 (State-space, Fluid Systems, Thermal Systems, Frequency Response) plus mechanical EOM/TF derivation from prior lectures. Sections marked [EXAM 3] are weighted accordingly.

---

## 1. Variable Notation

### General system variables
- t — Time (sec)
- s — Laplace variable (1/sec)
- j — Imaginary unit, j = sqrt(-1)
- x(t) — Generic dependent variable / state
- u(t) — Input / forcing function
- y(t) — Output
- U(s), Y(s), X(s) — Laplace transforms of u, y, x
- G(s) — Transfer function
- 1(t) — Unit step function
- delta(t) — Unit impulse function
- K, k — Static gain (also called static sensitivity, DC gain)
- tau — Time constant (sec) [first-order systems]
- omega_n — Undamped natural frequency (rad/sec)
- omega_d — Damped natural frequency (rad/sec)
- omega_r — Resonant frequency (rad/sec)
- omega_c — Cut-off frequency (rad/sec) = 1/tau for 1st-order
- zeta (sometimes written xi) — Damping ratio (dimensionless)
- p, p_i — Poles of transfer function
- z, z_j — Zeros of transfer function
- A_i — Partial-fraction expansion residue / coefficient
- OS% — Percent overshoot (dimensionless or %)
- t_r — Rise time (sec)
- t_p — Peak time (sec)
- t_s — Settling time (sec), with band: t_s_1%, t_s_2%, t_s_5%
- T_d — Damped oscillation period (sec) = 2*pi/omega_d

### Translational mechanical (Lecture 7)
- m, M — Mass (kg)
- k, K — Spring stiffness (N/m)
- b, B — Damping coefficient, translational (N-s/m)
- x — Displacement (m)
- v — Velocity (m/s) = dx/dt
- a — Acceleration (m/s^2) = d^2x/dt^2
- f, F — Force (N)
- KE — Kinetic energy (J)
- PE — Potential energy (J)

### Rotational mechanical (Lecture 8)
- theta — Angular displacement (rad)
- omega — Angular velocity (rad/sec) = d(theta)/dt
- alpha — Angular acceleration (rad/sec^2) = d^2(theta)/dt^2
- I, J — Moment of inertia (kg-m^2)
- k_T — Torsional spring stiffness (N-m/rad)
- B, c_T — Torsional damping coefficient (N-m-s/rad)
- T, M, tau (torque symbol) — Torque (N-m)
- p — Power (N-m/sec) = W
- w — Work / energy (N-m or J)

### State-space (Lecture 10) [EXAM 3]
- x — State vector (n-row column vector)
- u — Input vector (m-row column vector)
- y — Output vector (p-row column vector)
- x_dot — dx/dt
- A — State matrix (n x n)
- B — Input matrix (n x m)
- C — State output matrix (p x n)
- D — Control output matrix / direct feedthrough matrix (p x m)
- n — System order (= number of states)

### Fluid systems (Lecture 11) [EXAM 3]
- p — Pressure (Pa)
- p_hat — Absolute pressure
- p_r — Reference pressure
- q_m — Mass flow rate (kg/sec)
- q_mi — Mass inflow rate (kg/sec)
- q_mo — Mass outflow rate (kg/sec)
- q_mr — Reference mass flow rate
- q_v — Volumetric flow rate (m^3/sec)
- m — Fluid mass (kg)
- h — Liquid height (m)
- h_hat — Absolute liquid height
- h_r — Reference liquid height
- A — Cross-sectional area of tank (m^2)
- R — Fluid resistance (Pa-s/kg)
- R_r — Linearized fluid resistance at reference point
- C — Fluid capacitance (kg/Pa)
- I — Fluid inertance (Pa-s^2/kg)
- rho — Fluid density (kg/m^3)
- g — Gravitational acceleration (9.81 m/s^2)
- mu — Dynamic viscosity (Pa-s)
- nu — Kinematic viscosity (m^2/s)
- Re — Reynolds number (dimensionless)
- A_o — Orifice area (m^2)
- C_d — Discharge coefficient (dimensionless, in (0,1])
- D — Pipe diameter (m)
- L — Pipe length (m)
- v_bar — Average flow velocity (m/s)

### Thermal systems (Lecture 12) [EXAM 3]
- T — Temperature (K or deg C)
- T_r — Reference temperature
- T_o — Surrounding / ambient temperature
- E — Stored heat energy (J)
- q — Heat flow rate (J/sec or W)
- q_in, q_out — Heat flow rate in/out (W)
- C — Thermal capacitance (J/K)
- R — Thermal resistance (K-sec/J or K/W)
- R_eq — Equivalent thermal resistance
- c_p — Specific heat (J/kg-K)
- k (when context = conduction) — Thermal conductivity (W/m-K)
- h_conv — Convective heat transfer coefficient (W/m^2-K)
- A — Surface area or cross-sectional area (m^2)
- d — Thickness (m)
- T_S — Surface temperature (K)
- T_F — Fluid temperature (K)

### Frequency response (Lecture 13) [EXAM 3]
- omega — Angular frequency of input sinusoid (rad/sec)
- G(j*omega) — Frequency response function
- |G(j*omega)| — Magnitude response
- angle(G(j*omega)) — Phase response (rad or deg)
- dB — Decibel (logarithmic gain measure)
- M_o — Output sinusoid amplitude
- A_o (in freq-response context) — Input sinusoid amplitude
- phi — Phase shift / phase angle

### Complex numbers (Lecture 2)
- z = x + j*y — Rectangular form
- z = A*exp(j*theta) — Polar/exponential form
- A = |z| = sqrt(x^2 + y^2) — Magnitude
- theta = angle(z) — Phase angle
- atan2(y,x) — Four-quadrant arctangent (MATLAB function)

---

## 2. Core Methods & Procedures

### Transfer Function Derivation from Physical System (Lecture 4)
Steps:
1. Set up the differential equation(s) via physics-based modeling (Newton's 2nd law for mechanical, mass/heat/energy conservation for fluid/thermal).
2. Identify input and output variables.
3. Take Laplace transform on both sides assuming ZERO initial conditions.
4. Manipulate the algebraic equation containing input and output Laplace transforms.
5. Compute the ratio Y(s)/U(s) — this is the transfer function.
Key rule: Zero ICs are mandatory for transfer function definition.

### ODE Solution via Laplace Transform (Lecture 4)
Steps:
1. Take Laplace transform of the ODE, including initial conditions for derivatives.
2. Solve the resulting algebraic equation for Y(s).
3. Y(s) splits into forced response (due to input U(s)) and free response (due to ICs).
4. Apply partial fraction expansion (PFE) to Y(s).
5. Apply inverse Laplace transform term-by-term using the Laplace transform table.
Key rule: Use 0-minus as lower integration limit to handle impulses and discontinuous derivatives.

### Partial Fraction Expansion (Lecture 3)
Case I — Distinct real roots: Y(s) = sum over i of A_i/(s - p_i) where A_i = lim (s -> p_i) of [(s - p_i) * Y(s)].
Case II — Repeated roots: For an n-fold root at s = p, expand as A_1/(s-p)^n + A_2/(s-p)^(n-1) + ... + A_n/(s-p); compute A_i using the residual formula with derivatives.
Case III — General case: Mix of distinct and repeated.
Case V — Complex conjugate roots: Compute residue A at complex root, then use 2*Re{A*exp(p*t)} = 2*exp(real(p)*t)*[A_real*cos(imag(p)*t) - A_imag*sin(imag(p)*t)].
Preliminary: If order(numerator) >= order(denominator), do polynomial division first to get strictly proper rational function + quotient.
Key rule: For complex-conjugate pole pairs, the two residues are complex conjugates; combine via 2*Re{...}.

### Step-Response Analysis of 1st-Order System (Lecture 5)
Steps:
1. Identify K (static gain) from steady-state output / step input amplitude.
2. Identify tau (time constant) from time at which y reaches 63.2% of steady-state value.
3. Equivalent: At t = tau, y = 0.632*K*A. At t = 4*tau, y = 0.982*K*A.
4. Pole location: s = -1/tau.
Key rule: Larger tau means slower convergence to steady state.

### Step-Response Analysis of Underdamped 2nd-Order System (Lecture 5)
Steps:
1. Identify static gain k from steady-state output y_ss / step input magnitude A: k = y_ss/A.
2. Measure OS% (overshoot percent) and compute zeta: zeta = sqrt(ln(OS%)^2 / (pi^2 + ln(OS%)^2)).
3. Measure damped oscillation period T_d from response; compute omega_d = 2*pi/T_d.
4. Compute omega_n = omega_d / sqrt(1 - zeta^2).
5. For mass-spring-damper TF 1/(M*s^2 + b*s + K): K_stiffness = M*omega_n^2, b = 2*zeta*omega_n*M.
Key rule: In this class, use the SIMPLE relation t_r = 1.8/omega_n for rise time (not the linear or higher-order approximations).

### Pole Location and Transient Performance Mapping (Lecture 6)
Mapping (2nd-order, complex conjugate pole at -zeta*omega_n +/- j*omega_d):
- Rise time t_r = 1.8/omega_n: inversely related to radius of pole vector from origin.
- Peak time t_p = pi/omega_d: inversely related to imaginary part (omega_d).
- 2% settling time t_s = 4/(zeta*omega_n): inversely related to real part (zeta*omega_n).
- OS% = exp(-zeta*pi / sqrt(1 - zeta^2)) * 100%: depends only on radial direction angle of pole vector (zeta = sin(beta) where beta is angle from imaginary axis).
Key rule: All poles must have negative real part for stability. Even one right-half-plane pole means unstable.

### Translational Mechanical EOM Derivation (Lecture 7)
Steps:
1. Draw free body diagram (FBD) for each mass; identify all forces (spring restoring, damping, external).
2. Choose absolute coordinates with consistent positive direction.
3. Apply Newton's 2nd law: sum of forces = m*x_double_dot for each mass.
4. Substitute spring force = k*(deflection) and damper force = b*(velocity difference); use sign convention based on assumed deformation direction.
5. Rearrange to standard form: M*x_ddot + B*x_dot + K*x = f(t).
6. For multi-DOF: write coupled ODEs, take Laplace, solve algebraically for desired TF.
Key rule: When two masses interact via spring/damper, force on mass 1 from spring is k*(x_2 - x_1) and damper is b*(x_2_dot - x_1_dot); equal and opposite on mass 2.

### Rotational Mechanical EOM Derivation (Lecture 8)
Steps:
1. Identify rotational inertias I_i and their angular displacements theta_i.
2. Sum moments about each rotation axis: I*theta_ddot = sum of torques.
3. Torsional spring torque = k_T * (theta_difference); torsional damper torque = c_T * (omega_difference).
4. Apply parallel axis theorem if rotating about non-centroidal axis: J = J_O + M*r^2.
5. For fixed-end shaft: I_e = I_c + I_d/3 (one-third of distributed inertia adds).
Key rule: Use Newton's 3rd law for action-reaction torques between coupled inertias.

### Block Diagram Reduction (Lecture 9)
Steps:
1. Series blocks: G_eq = G_1 * G_2.
2. Parallel blocks: G_eq = G_1 + G_2.
3. Negative feedback: closed-loop TF = G_1 / (1 + G_1*G_2).
4. Positive feedback: closed-loop TF = G_1 / (1 - G_1*G_2).
5. For deriving TF directly from block diagram: start at output, trace backward through summers, stop when output reappears; ensure all blocks are included.
Key rule: Multiple inputs (reference + disturbance) — derive each TF separately by setting other inputs to zero (linear superposition).

### State-Space Model Derivation from ODE [EXAM 3] (Lecture 10)
Steps:
1. For an n-th order ODE in output y, define n state variables: x_1 = y, x_2 = y_dot, x_3 = y_ddot, ..., x_n = y^(n-1).
2. Write n first-order ODEs: x_1_dot = x_2, x_2_dot = x_3, ..., x_(n-1)_dot = x_n, x_n_dot = (rearranged ODE).
3. Assemble matrix form: x_dot = A*x + B*u, where A is (n x n), B is (n x m).
4. Write output equation: y = C*x + D*u, where C selects/combines states for output, D is feedthrough (often zero).
5. For coupled multi-input multi-output (MIMO) systems, define states from physical insight (e.g., heights, temperatures) and write each x_i_dot from the underlying ODE.
Key rule: Number of states = system order = highest derivative order. Convert from TF to state-space in MATLAB via ss(G).

### Fluid System Modeling: Tank Problems [EXAM 3] (Lecture 11)
Steps:
1. Apply continuity (conservation of fluid mass) to each tank: d(rho*A_i*h_i)/dt = q_m_in - q_m_out.
2. For constant rho and A_i: rho*A_i*(dh_i/dt) = q_m_in - q_m_out.
3. Use deviation variables relative to equilibrium reference (h_hat = h_r + h, q_hat = q_r + q_dev).
4. At equilibrium, internal flows are zero (q_1mr = 0), inflow = outflow (q_mir = q_mor).
5. For laminar/linear resistance: q_m_through_R = rho*g*(h_1 - h_2)/R (between two tanks at heights h_1, h_2).
6. The factor rho often cancels out — final ODE is in heights only.
7. For each tank produce one first-order ODE; combine to obtain coupled system.
8. Take Laplace transform with zero ICs to get transfer functions.
9. State-space: choose states x_1 = h_1, x_2 = h_2 (one state per tank).
Key rule: ONE order-of-ODE per tank/container. Watch for nonlinearity — turbulent outflow q_m = (rho/R)*sqrt(p) is NONLINEAR and may require linearization.

### Fluid Resistance Linearization (Lecture 11)
Steps:
1. Express nonlinear relation: p_hat = f(q_m_hat).
2. Take 1st-order Taylor expansion about reference (q_mr, p_r): p_hat - p_r = R_r * (q_m_hat - q_mr), where R_r = dp_hat/dq_m_hat evaluated at reference.
3. Define deviation variables p = p_hat - p_r, q_m = q_m_hat - q_mr.
4. Linearized: q_m = p/R_r.
Key rule: R_r depends on reference operating point (q_mr, p_r); it is local, not global.

### Thermal System Modeling [EXAM 3] (Lecture 12)
Steps:
1. Apply conservation of heat energy to each thermal mass: C_i * dT_i/dt = q_in - q_out.
2. Use Newton's law of cooling for each heat-flow path: q = (T_hot - T_cold) / R.
3. For multiple thermal masses: write coupled first-order ODEs in temperatures.
4. Combine into ODE form; take Laplace transform with zero ICs for transfer function.
5. State variables: choose x_i = T_i (one state per thermal capacitance).
6. Treat large external bodies (surroundings) as ideal temperature sources with infinite capacitance.
Key rule: ONE order-of-ODE per thermal capacitance. Heat flow direction: from higher to lower temperature.

### Conduction Resistance Calculation (Lecture 12)
Steps:
1. For a slab of thickness d and area A with conductivity k: R = d / (k*A).
2. For convection at surface with coefficient h_conv and area A: R = 1 / (h_conv*A).
3. Resistances in series (heat flows through in sequence): R_eq = R_1 + R_2 + ...
4. Resistances in parallel (heat flows through both simultaneously): 1/R_eq = 1/R_1 + 1/R_2 + ...
Key rule: Series total > any individual; parallel total < any individual.

### Frequency Response Function from Transfer Function [EXAM 3] (Lecture 13)
Steps:
1. Substitute s = j*omega in G(s): G(j*omega) = G(s)|_{s = j*omega}.
2. Magnitude response: |G(j*omega)| = sqrt(Re{G}^2 + Im{G}^2).
3. Phase response: angle(G(j*omega)) = atan2(Im{G}, Re{G}).
4. Convert magnitude to dB: dB = 20*log10(|G(j*omega)|).
5. For Bode plot interpretation: magnitude in dB vs. log(omega); phase in degrees vs. log(omega).
Key rule: For a stable LTI system under sinusoidal input u(t) = A*sin(omega*t), steady-state output is y_ss(t) = A*|G(j*omega)|*sin(omega*t + angle(G(j*omega))). The frequency does not change; only amplitude and phase are modified.

### Steady-State Output under Sinusoidal Input via Bode Plot [EXAM 3] (Lecture 13)
Steps:
1. Locate the input frequency omega on the Bode plot horizontal axis.
2. Read magnitude response in dB; convert to linear gain via Gain = 10^(dB/20).
3. Read phase response in degrees; convert to radians if needed: phi_rad = phi_deg * pi/180.
4. Steady-state output: y_ss(t) = (input_amplitude) * Gain * sin(omega*t + phi_input + phi_response).
5. For multi-component input (sum of sinusoids at different frequencies): apply linear superposition — evaluate Bode response at each frequency independently and sum.
Key rule: Linear systems do NOT shift frequency; nonlinear systems can produce harmonics and frequency shifts.

---

## 3. Formulas & Equations

### Laplace transform basics (Lecture 3)
- Laplace transform definition: X(s) = integral from 0-minus to infinity of x(t)*exp(-s*t) dt
- Differentiation: L{dx/dt} = s*X(s) - x(0)
- Second derivative: L{d^2x/dt^2} = s^2*X(s) - s*x(0) - x_dot(0)
- n-th derivative (zero ICs): L{d^n x/dt^n} = s^n * X(s)
- Integration: L{integral from 0 to t of f(tau) d(tau)} = F(s)/s
- Initial Value Theorem (IVT): x(0+) = lim (s -> infinity) of s*X(s)
- Final Value Theorem (FVT): x(infinity) = lim (s -> 0) of s*X(s), applies ONLY when x(infinity) exists

### Laplace transform table (used in this course)
- L{delta(t)} = 1
- L{1(t)} = 1/s
- L{c} = c/s (constant)
- L{1(t - D)} = exp(-s*D)/s (shifted step)
- L{t^n} = n! / s^(n+1)
- L{exp(-a*t)} = 1/(s+a)
- L{(1/(n-1)!) * t^(n-1) * exp(-a*t)} = 1/(s+a)^n
- L{sin(b*t)} = b/(s^2 + b^2)
- L{cos(b*t)} = s/(s^2 + b^2)
- L{exp(-a*t)*sin(b*t)} = b/((s+a)^2 + b^2)
- L{exp(-a*t)*cos(b*t)} = (s+a)/((s+a)^2 + b^2)
- L{1 - exp(-a*t)} = a / (s*(s+a))
- L{sinh(b*t)} = b/(s^2 - b^2)

### Complex numbers (Lecture 2)
- Rectangular: z = x + j*y
- Polar/Euler: z = A*exp(j*theta) = A*(cos(theta) + j*sin(theta))
- Euler identity: exp(j*theta) = cos(theta) + j*sin(theta)
- Magnitude: A = sqrt(x^2 + y^2)
- Phase: theta = atan2(y, x) (use four-quadrant: tan^(-1)(y/x) for 1st/4th quadrant, add or subtract pi for 2nd/3rd)
- Result range of phase: (-pi, pi]

### First-order system (Lecture 5)
- ODE: tau*y_dot + y = K*u
- Transfer function: G(s) = K/(tau*s + 1)
- Pole: s = -1/tau
- Step response (input u = A): y(t) = K*A*(1 - exp(-t/tau))
- At t = tau: y = 0.632*K*A
- At t = 4*tau: y = 0.982*K*A
- Initial slope of step response: dy(0)/dt = K*A/tau = y_ss/tau

### Second-order system (Lecture 5, 6)
- Standard ODE: y_ddot + 2*zeta*omega_n*y_dot + omega_n^2*y = k*omega_n^2*u
- Transfer function (standard form): G(s) = k*omega_n^2 / (s^2 + 2*zeta*omega_n*s + omega_n^2)
- Characteristic roots / poles: s_1,2 = -zeta*omega_n +/- omega_n*sqrt(zeta^2 - 1)
- Underdamped (zeta < 1): s_1,2 = -zeta*omega_n +/- j*omega_n*sqrt(1 - zeta^2)
- Critically damped (zeta = 1): s_1,2 = -omega_n (repeated)
- Overdamped (zeta > 1): two distinct negative real roots
- Damped natural frequency: omega_d = omega_n*sqrt(1 - zeta^2)
- Resonant frequency (zeta < 0.707): omega_r = omega_n*sqrt(1 - 2*zeta^2)
- Damped oscillation period: T_d = 2*pi/omega_d
- For mass-spring-damper M*x_ddot + c*x_dot + K*x = f: omega_n = sqrt(K/M), zeta = c/(2*sqrt(M*K)), static gain = 1/K

### Step-response performance indices [USE THESE EXACT FORMS] (Lecture 5, 6)
- Rise time: t_r = 1.8/omega_n  [simple relation — use this one in this class]
- Peak time: t_p = pi/omega_d
- 1% settling time: t_s_1% = 4.6/(zeta*omega_n)
- 2% settling time: t_s_2% = 4/(zeta*omega_n)
- 5% settling time: t_s_5% = 3/(zeta*omega_n)
- Percent overshoot: OS% = exp(-zeta*pi/sqrt(1 - zeta^2)) * 100%
- Damping ratio from OS%: zeta = |ln(OS%_decimal)| / sqrt(pi^2 + ln(OS%_decimal)^2)
- Underdamped step response (input amplitude A): y(t) = K*A*[1 - (1/sqrt(1-zeta^2))*exp(-zeta*omega_n*t)*cos(omega_d*t - phi)], where tan(phi) = zeta/sqrt(1-zeta^2)
- Peak output: y_p = y_f + (y_f - y_0)*exp(-zeta*pi/sqrt(1-zeta^2))
- Static gain interpretation: y_ss = k * A (for step input of amplitude A)

### Translational mechanical (Lecture 7)
- Newton's 2nd law: m*a = m*(dv/dt) = sum of forces
- Hooke's law: f_spring = k*x (k = stiffness in N/m)
- Damping force: f_damper = b*v = b*(dx/dt)
- Coil spring stiffness: k = G*d^4 / (64*n*R^3)
- Mass-spring-damper EOM: m*x_ddot + b*x_dot + k*x = f(t)
- Mass-spring-damper TF (force to displacement): X(s)/F(s) = 1/(m*s^2 + b*s + k)
- Force-to-velocity TF: V(s)/F(s) = s/(m*s^2 + b*s + k)
- Kinetic energy: KE = (1/2)*m*v^2
- Potential energy (spring): PE = (1/2)*k*x^2
- Two-mass coupled (one between two springs/dampers): m_1*x_1_ddot + (b_1+b_2)*x_1_dot + (k_1+k_2)*x_1 - b_2*x_2_dot - k_2*x_2 = f_1(t)

### Rotational mechanical (Lecture 8)
- Newton's 2nd law (rotational): I*alpha = I*(d^2 theta/dt^2) = sum of torques
- Torsional spring torque: tau_spring = k_T * (theta_2 - theta_1)
- Torsional damping torque: tau_damper = c_T * (omega_2 - omega_1)
- Rotational EOM: I*theta_ddot + B*theta_dot + k_T*theta = T(t)
- Kinetic energy (rotational): KE = (1/2)*I*omega^2
- Parallel axis theorem: J = J_O + M*r^2
- Moment of inertia, sphere: I_G = (2/5)*m*R^2
- Mass rotating about point O at distance R: I_O = m*R^2
- Hollow cylinder about axis: I_x = (1/2)*m*(R^2 + r^2)
- Slender rod about end: J = (1/3)*M*L^2; about centroid: (1/12)*M*L^2
- Fixed-end shaft equivalent inertia: I_e = I_c + I_d/3 (one-third of distributed inertia)
- Petrov's law (bearing damping): c_T = pi*mu*D^3*L / (4*delta)

### Block diagram reductions (Lecture 9)
- Series: Y/U = G_1 * G_2
- Parallel: Y/U = G_1 + G_2
- Negative feedback: Y/R = G_1 / (1 + G_1*G_2)
- Positive feedback: Y/R = G_1 / (1 - G_1*G_2)
- Standard unity-feedback closed-loop: Y/R = G(s) / (1 + G(s))

### State-space [EXAM 3] (Lecture 10)
- State equation: x_dot = A*x + B*u
- Output equation: y = C*x + D*u
- Matrix dimensions: x is n-by-1, u is m-by-1, y is p-by-1, A is n-by-n, B is n-by-m, C is p-by-n, D is p-by-m
- For n-th order ODE with output y: x_1 = y, x_2 = y_dot, ..., x_n = y^(n-1); x_1_dot = x_2, ..., x_(n-1)_dot = x_n; x_n_dot solved from the original ODE.
- MATLAB: sys = ss(A, B, C, D); Gss = ss(G) converts from TF; lsim(sys, u, t, x0) plots response with IC x0; initial(sys, x0) plots free response.

### Fluid system formulas [EXAM 3] (Lecture 11)
- Hydraulic analogy: pressure p ~ voltage v; mass flow rate q_m ~ current i; fluid mass m ~ charge Q.
- Fluid linear resistance: R = p/q_m (linearized at reference: R_r = dp/dq_m evaluated at reference)
- Fluid capacitance: C = m/p, equivalently C = dm/dp at reference
- Storage tank (vertical sides) capacitance: C = rho*A/g (where A = horizontal cross-section, g = gravity)
- Pressure due to liquid column: p = rho*g*h
- Mass stored in vertical tank: m = rho*A*h
- Fluid inertance: I = p / (dq_m/dt)
- Laminar pipe (Hagen-Poiseuille): R = 128*mu*L / (pi*rho*D^4), valid for Re < 2300
- Reynolds number: Re = rho*v_bar*D/mu = v_bar*D/nu (circular pipe)
- Average velocity in circular pipe: v_bar = q_v / (pi*D^2/4)
- Torricelli's principle (orifice outflow): q_m = C_d*A_o*sqrt(2*rho*p) = C_d*A_o*sqrt(2*g*rho^2*h) (NONLINEAR)
- Turbulent resistance: p_1 - p_3 = R*q_m^2 (NONLINEAR, but obeys series law in adding R's: R_total = R_1 + R_2 + ...)
- Mass conservation for single tank (vertical sides): rho*A*(dh/dt) = q_mi - q_mo
- Two connected tanks (linear resistance between, both vertical): 
  - Tank 1: A_1*(dh_1/dt) = -(g/R_1)*(h_1 - h_2)
  - Tank 2: A_2*(dh_2/dt) = q_mi/rho + (g/R_1)*(h_1 - h_2) - (g/R_2)*h_2
- V-shaped trough cross-sectional area at height h: A(h) = 2*L*h*tan(theta), where theta = half-angle. (NONLINEAR — area varies with h.)

### Thermal system formulas [EXAM 3] (Lecture 12)
- Stored heat energy: E = m*c_p*(T - T_r)
- Thermal capacitance: C = dE/dT = m*c_p = rho*V*c_p (units: J/K)
- Newton's law of cooling: q = (T_1 - T_2) / R = (delta_T) / R
- Thermal resistance, conduction: R = d / (k*A) (slab of thickness d, conductivity k, area A)
- Thermal resistance, convection: R = 1 / (h_conv * A)
- Resistances in series: R_eq = R_1 + R_2 + ... (total > any individual)
- Resistances in parallel: 1/R_eq = 1/R_1 + 1/R_2 + ... (total < any individual)
- Heat flow through wall + window (parallel paths): 1/R_eq = 1/R_wall + 1/R_window
- Single thermal mass with input heat: C*(dT/dt) = q_in - (T - T_surroundings)/R
- Two thermal masses (one inside the other) — quenching example:
  - Inner: C*(dT/dt) = -(1/R_1)*(T - T_b)
  - Outer (bath): C_b*(dT_b/dt) = (1/R_1)*(T - T_b) - (1/R_2)*(T_b - T_o)
- Two adjacent masses with shared wall, surroundings at T_o:
  - dT_1/dt = -(1/(R_1*C_1) + 1/(R_2*C_1))*T_1 + (1/(R_2*C_1))*T_2 + (1/(R_1*C_1))*T_o
  - dT_2/dt = (1/(R_2*C_2))*T_1 - (1/(R_2*C_2))*T_2

### Frequency response formulas [EXAM 3] (Lecture 13)
- Frequency response function: G(j*omega) = G(s) evaluated at s = j*omega
- Real and imaginary parts: G(j*omega) = Re{G(j*omega)} + j*Im{G(j*omega)} = R(omega) + j*X(omega)
- Magnitude: |G(j*omega)| = sqrt(R^2 + X^2) = sqrt(Re{G}^2 + Im{G}^2)
- Phase: angle(G(j*omega)) = atan2(Im{G}, Re{G}) = atan2(X, R)
- Magnitude in dB: dB = 20*log10(|G(j*omega)|)  [or equivalently 20*log10(A_out/A_in)]
- Linear gain from dB: Gain = 10^(dB/20)
- Useful dB conversions: 0 dB = 1, 6 dB ~ 2, 20 dB = 10, 40 dB = 100, -3 dB ~ 0.707, -6 dB = 0.5, -20 dB = 0.1
- Steady-state output under sinusoidal input u(t) = A*sin(omega*t + phi_u):
  y_ss(t) = A * |G(j*omega)| * sin(omega*t + phi_u + angle(G(j*omega)))
- For sum-of-sinusoids inputs: apply linear superposition; evaluate response at each frequency component separately.
- First-order frequency response G(s) = K/(tau*s+1):
  - |G(j*omega)| = K / sqrt(1 + (omega*tau)^2)
  - angle(G(j*omega)) = -atan(omega*tau)
  - At DC (omega = 0): |G| = K (= 20*log10(K) dB), phase = 0 deg
  - At cut-off omega_c = 1/tau: |G| = K/sqrt(2) (i.e., -3 dB from DC), phase = -45 deg
  - At omega -> infinity: |G| -> 0 (-infinity dB), phase -> -90 deg
- Second-order frequency response G(s) = k*omega_n^2/(s^2 + 2*zeta*omega_n*s + omega_n^2):
  - |G(j*omega)| = k / sqrt((1 - (omega/omega_n)^2)^2 + (2*zeta*omega/omega_n)^2)
  - angle(G(j*omega)) = -atan2(2*zeta*omega/omega_n, 1 - (omega/omega_n)^2)
  - At DC: |G(j0)| = k (static gain)
  - At omega = omega_n: |G(j*omega_n)| = k/(2*zeta), phase = -90 deg
  - Resonant peak (zeta < 0.707): omega_r = omega_n*sqrt(1 - 2*zeta^2), |G(j*omega_r)| = k / (2*zeta*sqrt(1 - zeta^2))
  - For large omega: |G| decreases at -40 dB/decade asymptotic slope; phase approaches -180 deg.
- MATLAB: bode(G), or bode(num, den), or H = freqresp(sys, w); abs(H); phase(H)

### Pure time delay (HW12 reference)
- Transfer function: exp(-s*D) where D = delay in seconds
- Frequency response: |exp(-j*omega*D)| = 1, angle = -omega*D (linear phase loss)

---

## 4. Standard Assumptions & Idealizations

- Zero initial conditions when deriving any transfer function (assumed unless explicitly stated otherwise).
- Linear time-invariant (LTI) behavior unless the problem flags a nonlinearity.
- Springs are massless and obey Hooke's law (linear: f = k*x).
- Dampers are massless and linear (force proportional to relative velocity).
- Rigid bodies / rigid masses unless deformation is specifically modeled.
- Small displacements unless otherwise noted (justifies linearization).
- For rotational systems, treat shafts as torsional springs with own inertia ignored unless specified.
- For fluid systems: fluid density rho is constant; gravity g = 9.81 m/s^2.
- Tanks have vertical sides unless geometry specified otherwise (so cross-sectional area A is independent of height h, capacitance C = rho*A/g is constant).
- Flow is laminar unless turbulence is specified; laminar => linear pressure-flow.
- For deviation-variable models: linearize about an equilibrium reference; at equilibrium, internal inter-tank flows are zero and inflow = outflow.
- Thermal: specific heat c_p is constant (small variation); thermal capacitance C = m*c_p = rho*V*c_p.
- Surroundings have infinite thermal capacitance (T_o is constant input).
- Newton's law of cooling assumed for ALL heat-flow paths (linear: q = delta_T / R).
- Conductive heat flow obeys Fourier's law with constant thermal conductivity.
- For frequency response analysis: system is stable (all poles in left half plane) so steady-state response under sinusoid is well-defined.
- For final value theorem applications: y(infinity) must exist (i.e., system is stable for that input).

---

## 5. Common Problem Archetypes

### [EXAM 3] State-Space Conversion from ODE
Given a single n-th order ODE, define states as successive derivatives of output (x_1 = y, x_2 = y_dot, ...). Write n first-order ODEs and assemble into x_dot = A*x + B*u, y = C*x + D*u. Output equation C row selects the appropriate state(s). For multiple outputs, C has multiple rows. D is usually zero unless input appears directly in output.

### [EXAM 3] Two-Tank Liquid System
Apply mass conservation per tank: rho*A_i*(dh_i/dt) = (mass flow in) - (mass flow out). Use linear resistance q_m = rho*g*(h_a - h_b)/R between tanks. The rho cancels. Each tank => one first-order ODE. Take Laplace with zero ICs to get TF H_2(s)/Q_mi(s). For state-space, states are heights x_1 = h_1, x_2 = h_2. Watch for nonlinearity (turbulent flow needs Rq_m^2 = delta_p; V-shaped trough has h-dependent area).

### [EXAM 3] Two-Thermal-Mass Problem
Apply heat conservation per mass: C_i*(dT_i/dt) = sum of (T_other - T_i)/R_path. Use Newton's law of cooling for every heat flow path. Each mass => one first-order ODE. For TF, take Laplace with zero ICs and eliminate intermediate temperature. State-space: x_1 = T_1, x_2 = T_2.

### [EXAM 3] Frequency Response from Transfer Function
Substitute s = j*omega in G(s). Simplify numerator and denominator into rectangular form (a + j*b). Magnitude = sqrt(num_mag^2)/sqrt(den_mag^2). Phase = phase(num) - phase(den). Evaluate behavior at omega -> 0 (DC gain) and omega -> infinity (high-frequency asymptote).

### [EXAM 3] Sinusoidal Input via Transfer Function or Bode Plot
Given u(t) = A*sin(omega_0*t + phi_0) and G(s), compute |G(j*omega_0)| and angle(G(j*omega_0)). Steady-state output: y_ss(t) = A*|G(j*omega_0)|*sin(omega_0*t + phi_0 + angle(G(j*omega_0))). For multi-frequency inputs, apply superposition. When using a Bode plot, read dB at omega_0, convert via Gain = 10^(dB/20), and read phase directly.

### Mass-Spring-Damper EOM and TF (pre-Exam-3 review)
Draw FBD, apply Newton's 2nd law. Standard form: m*x_ddot + b*x_dot + k*x = f. TF: X(s)/F(s) = 1/(m*s^2 + b*s + k). Identify omega_n = sqrt(k/m), zeta = b/(2*sqrt(m*k)). Step response: use simple-relation transient indices (t_r = 1.8/omega_n, t_p = pi/omega_d, t_s_2% = 4/(zeta*omega_n), OS% from zeta).

### Rotational Mass-Spring-Damper (Lecture 8)
Sum moments about rotation axis: I*theta_ddot + B*theta_dot + k_T*theta = T(t). Identical form to translational; apply 2nd-order analysis. Use parallel-axis theorem if rotation not about centroid. For shafts with distributed inertia and fixed end, add I_d/3 to concentrated inertia.

### Coupled Two-DOF Mechanical System
Write FBD and EOM for each mass. Take Laplace transform with zero ICs of both equations. Solve algebraically: eliminate the unwanted variable from one equation to get TF for desired output / input. Result is typically 4th-order denominator.

### Block Diagram TF Derivation (Multi-Input)
For each input (reference, disturbance), set the others to zero and derive TF separately. Use feedback rule (G/(1 +/- G*H)). For final time response use linear superposition. For step input with R(s) = 1/s, apply FVT: y(infinity) = lim s*Y(s) as s -> 0.

### Partial Fraction Expansion with Complex Conjugate Poles
Compute residue A at one complex pole (the other root has conjugate residue A*). In time domain, the contribution from the conjugate pair is 2*exp(real(p)*t) * [Re{A}*cos(imag(p)*t) - Im{A}*sin(imag(p)*t)]. Combine with other PFE terms for final y(t).

### Pole-Location Problem (s-plane Sketch)
Given constraints on t_r, t_p, t_s_2%, OS%, translate each to a constraint on omega_n, omega_d, real-part, or zeta. Each constraint defines a region in the s-plane (circle, vertical line, horizontal line, or radial wedge). The desired pole region is the intersection. Final pole must be in left-half plane for stability.

### Conductive/Convective Resistance Through Composite Wall
Identify all parallel and series paths. For wall + window, both convey heat in parallel: 1/R_eq = 1/R_wall + 1/R_window. For a wall with multiple layers, series: R_eq = R_layer1 + R_layer2 + ... Compute equivalent R, then use q = delta_T/R_eq.

### Fluid Resistance Linearization Around Operating Point
For nonlinear pressure-flow relation p_hat = f(q_m_hat) (e.g., turbulent or orifice), compute R_r = dp_hat/dq_m_hat at the reference (q_mr, p_r). Define deviation variables and apply linear relation q_m = p/R_r locally. Useful for converting nonlinear tank problems into LTI form near equilibrium.

---

End of MECH 3340 Reference.
