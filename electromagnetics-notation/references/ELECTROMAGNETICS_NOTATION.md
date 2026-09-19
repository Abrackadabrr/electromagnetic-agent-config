# Canonical Electromagnetic Notation

## Harmonic fields

Physical real fields are represented by complex amplitudes with time factor

`exp(-i*omega*t)`.

For source-free homogeneous isotropic media:

`curl E = +i*omega*mu*H`

`curl H = -i*omega*epsilon*E`

`k = omega*sqrt(epsilon*mu)` with the outgoing/passive branch selected
consistently with the material model.

## Green function

`R = |x-y|`

`G_k(x,y) = exp(+i*k*R)/(4*pi*R)`.

Away from `x=y`:

`grad_x G_k = -grad_y G_k`.

The outgoing far phase is `exp(+ikr)` under the project's `exp(-i*omega*t)`
time convention.

## Project K operator

For a source domain `Q`:

`K_Q[j](x) = grad_x div_x int_Q G_k(x,y) j(y) dQ_y
             + k^2 int_Q G_k(x,y) j(y) dQ_y`.

For surface currents, use surface/weak formulations appropriate to the chosen
trace and discretization rather than naively evaluating the second derivative
at a singular point.

For voxel PWC VIE, the codebase already exploits an equivalent decomposition in
which the `grad div` contribution is represented through component jumps across
voxel faces and the `k^2` term remains a volume Green integral.

## Project R operator

`R_Q[j](x) = int_Q grad_x G_k(x,y) cross j(y) dQ_y`.

Keep this cross-product order explicit. `a cross b = -(b cross a)`.

## Surface-current field representation used by the thesis

With the thesis definitions of electric and magnetic surface-current densities:

`E = +i/(omega*epsilon) K[J_e] - R[J_m]`

`H = R[J_e] + i/(omega*mu) K[J_m]`.

These prefactors are not universal current definitions. Re-derive them if the
unknown is a polarization current, contrast current, flux density, or another
quantity.

## Surface limiting formulas in the thesis convention

At a smooth non-edge point, for the thesis side/normal convention:

`(R[j])^+ = R[j] + 1/2 * (j cross n)`

`(R[j])^- = R[j] - 1/2 * (j cross n)`

and the stated K trace contains the corresponding surface-divergence jump.

Do not transplant these jump signs to another definition of `+/-`, normal, or
operator without re-deriving the mapping.
