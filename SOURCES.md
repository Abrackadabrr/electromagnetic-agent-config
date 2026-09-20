# Sources

## Canonical project source

The author's attached thesis is the canonical source for the project's
electromagnetic notation and the baseline surface discretization. The skill
repository does not vendor the PDF; the relevant conventions and algorithms are
captured in the references.

The thesis establishes:

- `exp(-i*omega*t)` time dependence;
- `F=exp(+ikR)/(4*pi*R)`;
- project operators `K` and `R`;
- the stated jump relations and plus/minus trace convention;
- field representations through electric and magnetic surface currents;
- PWC tangential currents with collocation on quadrilateral cells;
- structured matrices for translated repeated elements;
- block-Toeplitz storage, low-rank off-diagonal interactions, GMRES, and a
  block-diagonal preconditioner;
- regular-grid VIE and tensor/QTT methods as natural future structured-matrix
  research directions.

## Surface integral equations

- S. M. Rao, D. R. Wilton, A. W. Glisson, “Electromagnetic scattering by
  surfaces of arbitrary shape,” IEEE TAP 30(3), 409-418, 1982,
  DOI 10.1109/TAP.1982.1142818.
- W. C. Gibson, *The Method of Moments in Electromagnetics*.
- J. L. Volakis, K. Sertel, *Integral Equation Methods for Electromagnetics*.
- D. Colton, R. Kress, *Integral Equation Methods in Scattering Theory*.

## Volume integral equations

- D. H. Schaubert et al., “A tetrahedral modeling method for electromagnetic
  scattering by arbitrarily shaped inhomogeneous dielectric bodies,” IEEE TAP
  32(1), 77-85, 1984, DOI 10.1109/TAP.1984.1143193.
- M. I. Sancer et al., “On Volume Integral Equations,” IEEE TAP 54(5),
  1488-1495, 2006, DOI 10.1109/TAP.2006.874316.
- A. G. Polimeridis, J. F. Villena, L. Daniel, J. K. White, “Stable FFT-JVIE
  solvers for fast analysis of highly inhomogeneous dielectric objects,” JCP
  269, 280-296, 2014, DOI 10.1016/j.jcp.2014.03.026.
- I. P. Georgakis et al., “A Fast Volume Integral Equation Solver with Linear
  Basis Functions for the Accurate Computation of Electromagnetic Fields in
  MRI,” arXiv:1902.02196.

## Coupled surface-volume equations

- N. Yuan, T. S. Yeo, X. C. Nie, L. W. Li, “RCS Computation of Composite
  Conducting-Dielectric Objects with Junctions using the Hybrid Volume-Surface
  Integral Equation,” JEMWA 19(1), 19-36, 2005,
  DOI 10.1163/1569393052955107.
- X. Nie et al., “A fast volume-surface integral equation solver for scattering
  from composite conducting-dielectric objects,” IEEE TAP 53(2), 818-824,
  2005, DOI 10.1109/TAP.2004.841323.
- C. Luo, C.-C. Lu, “Electromagnetic Scattering Computation Using a Hybrid
  Surface and Volume Integral Equation Formulation,” ACES Journal 22(3),
  340-349, 2007.

## Structured operators

The thesis bibliography explicitly includes A. G. Polimeridis et al. (2014)
for regular-grid FFT-JVIE and D. V. Savostyanov / E. E. Tyrtyshnikov work on
multilevel special matrix formats in electrodynamics. The thesis conclusion
also identifies preconditioning and tensor/QTT representations as future
research directions.
