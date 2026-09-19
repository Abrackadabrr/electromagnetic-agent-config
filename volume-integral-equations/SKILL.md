---
name: volume-integral-equations
description: Electromagnetic VIE/JVIE/DVIE formulations for inhomogeneous media and coupled surface-volume integral equations.
---

# Volume Integral Equations

Also load `electromagnetics-notation`.

Load `operator-discretization` for matrix assembly. Load `uniform-grid-vie` for
Cartesian voxel grids.

## First rule: define the unknown

Before writing a VIE, state whether the unknown is `E`, `D`, polarization or
contrast current `J`, magnetization current, or a coupled electric/magnetic
current pair. Different unknowns produce different identity/material terms and
conditioning.

## Project operator family

Use the same project `K` kernel family on volume domains:

`K_V[j] = grad div int_V G j dV + k^2 int_V G j dV`.

Derive physical prefactors from Maxwell and the selected unknown definition.

For example, with `exp(-i*omega*t)`, if polarization current is explicitly
defined by `J_p = dP/dt`, then
`J_p = -i*omega*(epsilon-epsilon_b)*E`.
Do not use this relation if the code defines another contrast current.

## Coupled SIE-VIE / VSIE

Read `references/SIE_VIE_COUPLING.md` whenever both surface and volume unknowns
are present.

## References

Read `references/VIE_FORMULATIONS.md` for formulation families and literature.
