---
name: surface-integral-equations
description: Surface electromagnetic integral equations, equivalent currents, PEC/dielectric formulations, RWG or project PWC discretizations, and surface junctions.
---

# Surface Integral Equations

Also load `electromagnetics-notation`.

Load `operator-discretization` for matrix assembly or quadrature work.

## Scope

Support full-wave frequency-domain SIE formulations including PEC EFIE/MFIE/
CFIE, dielectric SIE/PMCHWT/Müller families, open surfaces, closed surfaces,
composite conducting/dielectric surfaces, and surface junctions.

## Discretization branches

Do not merge these branches silently:

1. project/thesis collocation with piecewise-constant tangential currents on
   quadrilateral/parallelogram cells;
2. classical triangular MoM with RWG basis and Galerkin testing.

Read:

- `references/SIE_FORMULATIONS.md`;
- `references/SURFACE_DISCRETIZATION.md`;
- `references/SURFACE_JUNCTIONS.md`.
