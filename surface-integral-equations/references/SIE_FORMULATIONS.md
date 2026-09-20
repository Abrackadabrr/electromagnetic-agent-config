# Surface integral-equation formulation cards

All equations below use the project `exp(-i*omega*t)` convention and project
K/R operators unless explicitly stated otherwise.

## 1. PEC electric-field equation in project notation

Assume a surface electric-current density J radiates

`E_J = i/(omega*epsilon_b) K_S[J]`.

For a PEC surface, impose the tangential total electric field condition:

`(E_inc + E_J)_tau = 0`.

Therefore the EFIE-like equation in project notation is

`i/(omega*epsilon_b) (K_S[J])_tau = -(E_inc)_tau`.

On an open PEC sheet, the boundary condition is imposed on the required sides;
do not add a closed-surface magnetic jump term merely because the geometry is a
surface mesh.

## 2. MFIE / CFIE warning

The exact MFIE identity depends on the definition of the surface-current
unknown (for example `n cross H` versus `H cross n`), normal direction, and
which R trace is used.

Do not hard-code a universal project MFIE from a memorized `1/2 I +/- K`
formula. Instead:

1. declare the current definition;
2. write `H=H_inc+R[J]`;
3. choose exterior/interior trace under the project plus/minus convention;
4. substitute the thesis R jump formula;
5. only then rearrange to MFIE;
6. form CFIE as the requested linear combination of already audited EFIE and
   MFIE equations.

This explicit derivation is safer than translating a named equation from a
different convention.

## 3. Thesis waveguide-port system

The thesis introduces:

- electric surface current `j_E` on the whole surface `Sigma`;
- magnetic surface current `j_M` on the port surface `Sigma_0`.

Fields:

`E = i/(omega*epsilon_0) K[Sigma,j_E] - R[Sigma_0,j_M]`;

`H = R[Sigma,j_E] + i/(omega*mu_0) K[Sigma_0,j_M]`.

The transformed Eq. (13) uses tangential components and the R jump term. When
implementing it, consult `electromagnetics-notation/references/THESIS_BASELINE.md`
because the printed third line contains a coefficient that must be re-audited
against Eq. (12) rather than copied blindly.

## 4. Dielectric surface-equivalent-current systems

For a closed penetrable interface separating two homogeneous regions:

1. choose one normal orientation and keep it globally fixed;
2. introduce electric and magnetic equivalent surface-current definitions;
3. write regional E/H representations using each region's `k,epsilon,mu`;
4. take the appropriate traces from each side;
5. enforce continuity of tangential E and H;
6. combine the two regional equations into the desired PMCHWT-, Müller-, or
   related system;
7. simplify jump terms only after current/normal/trace conventions are explicit.

External PMCHWT/Müller formulas are often written under different harmonic
conventions. Translate them through the notation skill before coding.

## 5. Formulation record required before implementation

Record:

- geometry: open/closed/composite;
- region material parameters;
- unknown current definitions;
- normal direction;
- observation side of every trace;
- project K/R field representation;
- boundary/continuity conditions;
- resulting block rows.

If any item is missing, derive it before assembling a matrix.
