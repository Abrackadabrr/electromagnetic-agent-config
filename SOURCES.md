# Source Notes

These references informed the integral-equation skills. Mathematical equations
must still be translated into the project's `exp(-i*omega*t)` convention before
use.

## Project source

- User thesis: canonical time convention, Green function, project K/R notation,
  field representation, PWC surface collocation, self/near treatment.
- `Abrackadabrr/Electromagnetic-Waves-Scattering`, branch `dev`: current C++
  architecture, operator helpers, voxel K implementation, `CubeMesh`, structured
  Toeplitz classes.
- `Abrackadabrr/ED-researh`, branch `dev`: research/examples repository. Only
  repository metadata/README were available during this configuration pass;
  inspect the local tree at runtime for detailed experiment conventions.

## Surface integral equations

- S. M. Rao, D. R. Wilton, A. W. Glisson, “Electromagnetic scattering by
  surfaces of arbitrary shape,” IEEE TAP 30(3), 409-418, 1982,
  DOI 10.1109/TAP.1982.1142818.
- W. C. Gibson, *The Method of Moments in Electromagnetics*.
- J. L. Volakis, K. Sertel, *Integral Equation Methods for Electromagnetics*.

## Volume integral equations

- D. H. Schaubert et al., “A tetrahedral modeling method for electromagnetic
  scattering by arbitrarily shaped inhomogeneous dielectric bodies,” IEEE TAP
  32(1), 77-85, 1984, DOI 10.1109/TAP.1984.1143193.
- M. I. Sancer et al., “On Volume Integral Equations,” IEEE TAP 54(5),
  1488-1495, 2006, DOI 10.1109/TAP.2006.874316.
- A. G. Polimeridis et al., “Stable FFT-JVIE solvers for fast analysis of highly
  inhomogeneous dielectric objects,” JCP 269, 280-296, 2014,
  DOI 10.1016/j.jcp.2014.03.026.
- I. P. Georgakis et al., “A Fast Volume Integral Equation Solver with Linear
  Basis Functions for the Accurate Computation of Electromagnetic Fields in
  MRI,” arXiv:1902.02196, 2019.

## Coupled volume-surface equations

- C. Luo, C.-C. Lu, “Electromagnetic Scattering Computation Using a Hybrid
  Surface and Volume Integral Equation Formulation,” ACES Journal 22(3),
  340-349, 2007.
- N. Yuan et al., “RCS Computation of Composite Conducting-Dielectric Objects
  with Junctions using the Hybrid Volume-Surface Integral Equation,” JEMWA
  19(1), 19-36, 2005, DOI 10.1163/1569393052955107.
- X. Nie et al., “A fast volume-surface integral equation solver for scattering
  from composite conducting-dielectric objects,” IEEE TAP 53(2), 818-824, 2005,
  DOI 10.1109/TAP.2004.841323.
