# Coupled Surface-Volume Integral Equations

## Block architecture

A VSIE/SIE-VIE formulation contains surface and volume unknowns in one integral
system. Keep the block semantics explicit:

`[ Z_SS  Z_SV ] [x_S] = [b_S]`
`[ Z_VS  Z_VV ] [x_V]   [b_V]`.

- `Z_SS`: surface sources observed/tested on the surface;
- `Z_SV`: volume sources observed/tested on the surface;
- `Z_VS`: surface sources observed/tested in the volume;
- `Z_VV`: volume sources observed/tested in the volume.

Cross blocks come from the same physical field representation as self blocks.
Do not invent them by transposing matrices unless reciprocity plus basis/testing
choices prove that relation.

## Typical mixed conducting/dielectric problem

One useful topology is:

- PEC represented by an equivalent electric surface current;
- inhomogeneous dielectric represented by an induced volume current or flux
  density;
- both source sets radiate through the same background Green function;
- PEC boundary conditions and dielectric volume constitutive equation supply the
  two block rows.

This keeps the dielectric out of a surface-equivalent-current description while
retaining a true surface current on the conductor.

## Junctions

A conductor-dielectric contact can require special surface/volume basis handling
near the shared geometry. The exact rule depends on unknown definitions and
conformity. Do not automatically import pure-SIE junction reduction rules into a
VSIE.

## Literature

- C. C. Lu and W. C. Chew (2000), coupled surface-volume integral equation for
  composite metallic/material targets (see citation chain in later VSIE papers).
- N. Yuan, T. S. Yeo, X. C. Nie, L. W. Li (2005), *RCS Computation of Composite
  Conducting-Dielectric Objects with Junctions using the Hybrid Volume-Surface
  Integral Equation*, JEMWA 19(1), 19-36,
  DOI 10.1163/1569393052955107.
- X. Nie et al. (2005), *A fast volume-surface integral equation solver for
  scattering from composite conducting-dielectric objects*, IEEE TAP 53(2),
  818-824, DOI 10.1109/TAP.2004.841323.
- C. Luo and C.-C. Lu (2007), *Electromagnetic Scattering Computation Using a
  Hybrid Surface and Volume Integral Equation Formulation*, ACES Journal 22(3),
  340-349.
