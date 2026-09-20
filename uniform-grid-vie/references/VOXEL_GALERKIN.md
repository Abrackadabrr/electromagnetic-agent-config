# Voxel Galerkin discretization

## PWC vector basis

On a uniform Cartesian grid, a PWC vector field normally has three Cartesian
component coefficients per active voxel.

For identical translated source/test voxels, each relative displacement
carries a small component-coupling block (typically 3x3 for a Cartesian vector
PWC basis).

## Operator decomposition

For the project K family:

`K[j] = grad div int_V F j dV + k_b^2 int_V F j dV`.

Do not evaluate the coincident grad-div term by ordinary Hessian quadrature.

For cellwise-constant volume fields, a useful weak/distributional
implementation represents the divergence contribution through jumps/fluxes on
voxel faces, while the `k_b^2` term remains a scalar Green volume potential.

Any such implementation must be derived for the exact testing normalization
used by the code.

## PWL extension

A discontinuous PWL basis adds local linear modes. It can improve field
accuracy but changes:

- block size;
- self/near integrals;
- moment tensors;
- FFT kernel-channel count.

Do not reuse PWC self corrections unchanged.

## Material map

For E-VIE:

`E - K_b[chi E] = E_inc`.

For J-VIE:

`J - chi K_b[J] = RHS`.

In both cases, keep the local chi multiplication logically separate from the
translation-invariant K_b interaction. This distinction is essential for
structured storage, preconditioning, and masked geometries.

## Validation ladder

1. one/two voxels: compare cell integrals with high-accuracy reference;
2. small dense grid: build full matrix explicitly;
3. displacement-based structured apply;
4. FFT apply;
5. analytic dielectric scatterer such as a sphere.

Do not proceed to large-scale timing before steps 1-4 agree.
