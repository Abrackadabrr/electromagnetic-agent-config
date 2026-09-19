# Volume Integral Equation Formulations

## Formulation families

Do not use “the VIE” as if it were unique. Common unknown choices include:

- E-field VIE (E-VIE);
- electric-flux-density VIE (D-VIE);
- equivalent-current / polarization-current VIE (J-VIE);
- potential formulations;
- coupled electric/magnetic volume-current formulations for simultaneous
  electric and magnetic contrast.

The unknown choice controls functional space, local material term, spectrum,
and natural discretization.

## Uniform Cartesian discretizations

For a voxel grid, important low-order choices are:

- PWC vector basis: 3 scalar component unknowns per active voxel;
- discontinuous PWL vector basis: commonly pulse plus x/y/z linear scalar modes
  per component, giving 12 coefficients per voxel.

Galerkin testing on identical translated voxels makes the homogeneous-background
Green interaction translationally invariant and suitable for Toeplitz/FFT
acceleration.

## Tetrahedral discretizations

For unstructured volumes, SWG-type divergence-conforming tetrahedral basis
functions are a classical option, especially for D-VIE/flux-density
formulations. Do not substitute SWG into a current formulation without checking
the required space and continuity.

## Derivative handling

Strongly singular `grad div` forms should not be implemented by direct numerical
second differentiation at coincident cells. Prefer a weak/integration-by-parts
form, face-jump representation for PWC voxels, or another source-verified
singularity reduction.

## Literature

- D. H. Schaubert, D. R. Wilton, A. W. Glisson et al. (1984), *A tetrahedral
  modeling method for electromagnetic scattering by arbitrarily shaped
  inhomogeneous dielectric bodies*, IEEE TAP 32(1), 77-85,
  DOI 10.1109/TAP.1984.1143193.
- M. I. Sancer, K. Sertel, J. L. Volakis, P. Van Alstine (2006), *On Volume
  Integral Equations*, IEEE TAP 54(5), 1488-1495,
  DOI 10.1109/TAP.2006.874316. Important for careful treatment of derivatives of
  discontinuous material functions.
- A. G. Polimeridis, J. F. Villena, L. Daniel, J. K. White (2014), *Stable
  FFT-JVIE solvers for fast analysis of highly inhomogeneous dielectric
  objects*, JCP 269, 280-296, DOI 10.1016/j.jcp.2014.03.026. Uniform-grid
  Galerkin equivalent-current VIE with FFT acceleration.
- I. P. Georgakis et al. (2019), *A Fast Volume Integral Equation Solver with
  Linear Basis Functions for the Accurate Computation of Electromagnetic Fields
  in MRI*, arXiv:1902.02196. Discontinuous PWL basis on uniform voxel grids.
