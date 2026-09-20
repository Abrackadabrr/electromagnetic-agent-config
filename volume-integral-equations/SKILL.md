---
name: volume-integral-equations
description: Derive, compare, or implement electromagnetic E-VIE/J-VIE/D-VIE formulations for penetrable inhomogeneous media and coupled surface-volume systems. Use when the volume unknown, contrast/material term, or SIE-VIE coupling matters; do not trigger for generic voxel FFT or matrix coding alone.
---

# Volume integral equations

Assume the project `exp(-i*omega*t)` convention and project K/R notation.

## First decision: define the unknown

Before writing a VIE, state whether the unknown is:

- electric field E;
- electric flux density D;
- polarization/equivalent current J;
- electric and magnetic contrast currents.

The identity/local material term and conditioning depend on this choice.

## Reference routing

- For formulation cards and conversion between E/J/D unknowns:
  read `references/VIE_FORMULATIONS.md`.
- For a mixed PEC-surface + dielectric-volume system:
  read `references/SIE_VIE_COUPLING.md`.
- For a Cartesian regular grid and translation-invariant voxel interactions:
  use `uniform-grid-vie`.
- For sign/current-convention translation:
  use `electromagnetics-notation`.

Do not call two equations “the same VIE” until their unknown definitions and
material normalizations have been matched.
