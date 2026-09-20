# Volume integral-equation formulation cards

This reference extends the thesis research direction to penetrable media. The
thesis itself does not derive these VIE equations; it cites regular-grid
FFT-JVIE as a natural structured-integral-equation example. The equations below
are therefore an extension written in the thesis/project convention.

Assume a nonmagnetic inhomogeneous dielectric in a homogeneous background:

- background `epsilon_b, mu_b`;
- `k_b=omega*sqrt(epsilon_b*mu_b)`;
- relative electric contrast
  `chi=(epsilon-epsilon_b)/epsilon_b`;
- project background operator `K_b` built with
  `F_b=exp(i*k_b*R)/(4*pi*R)`.

For `exp(-i*omega*t)`, define polarization/contrast current

`J = -i*omega*(epsilon-epsilon_b)*E
    = -i*omega*epsilon_b*chi*E`.

The background field radiated by J is

`E_J = i/(omega*epsilon_b) K_b[J]`.

Hence

`E = E_inc + i/(omega*epsilon_b) K_b[J]`.

## 1. E-VIE

Substitute J into the field representation:

`E - K_b[chi E] = E_inc`.

Important: for spatially varying chi, the multiplication by chi is inside the
source argument of K. Do not commute the material multiplier through the
translation-invariant Green operator.

### Implementation record

- unknown: E;
- local/material operation: source multiplication by chi;
- nonlocal operation: K_b;
- heterogeneous full operator is not globally Toeplitz even when K_b on a
  uniform grid is.

## 2. J-VIE

Use

`E = i J/(omega*epsilon_b*chi)`

only where chi is nonzero, or derive algebraically without dividing in vacuum.

From the field representation:

`J - chi K_b[J] = -i*omega*epsilon_b*chi*E_inc`.

This form is particularly natural for a dielectric support consisting only of
active contrast voxels.

### Implementation record

- unknown: J;
- local term: identity;
- local material multiplier: chi;
- nonlocal term: K_b[J];
- RHS: `-i*omega*epsilon_b*chi E_inc`.

Do not change the J definition without re-deriving all prefactors.

## 3. D-based formulation

Let `D=epsilon E` and define

`tau=(epsilon-epsilon_b)/epsilon = 1-epsilon_b/epsilon`.

Then

`J=-i*omega*tau*D`.

A D-VIE can be obtained by substituting this identity into the same background
field representation and multiplying by the chosen local material factors.

Because D-VIE literature uses several normalizations and operator scalings,
record the exact local multiplier and unknown normalization before coding.
Do not infer a D-VIE by renaming an E-VIE vector.

## 4. Magnetic contrast

If `mu != mu_b`, introduce the corresponding magnetic contrast source or use
a formulation derived for simultaneous electric/magnetic contrast. Do not
hide magnetic contrast inside the electric chi above.

## 5. Function-space/discretization choice

- Cartesian PWC/PWL: natural for voxelized regular-grid FFT approaches.
- Tetrahedral SWG-type bases: classical unstructured divergence-conforming
  volume option.

The selected unknown determines what continuity/conformity is physically and
numerically appropriate.

## 6. Validation

For a homogeneous dielectric sphere/cylinder where an analytic solution is
available:

1. refine the volume mesh;
2. compare fields or scattering quantities with the analytic solution;
3. verify the sign of the radiated field independently;
4. compare dense/reference and structured/FFT applications of K_b;
5. monitor residual and physically relevant observables separately.

## Literature

- Polimeridis, Villena, Daniel, White (JCP 2014): stable FFT-JVIE on voxel
  grids.
- Schaubert/Wilton/Glisson et al. (IEEE TAP 1984): tetrahedral dielectric
  volume modeling.
- Sancer/Sertel/Volakis/Van Alstine (IEEE TAP 2006): careful VIE formulation
  and material-derivative issues.
