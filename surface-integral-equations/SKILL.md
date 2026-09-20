---
name: surface-integral-equations
description: Derive, choose, or implement electromagnetic SIEs on PEC or dielectric surfaces, including EFIE/MFIE/CFIE-style equations, dielectric equivalent-current systems, waveguide-port currents, open/closed surfaces, RWG or PWC discretizations, and surface junctions. Do not trigger for pure VIE or generic Toeplitz/FFT coding.
---

# Surface integral equations

Assume the project `exp(-i*omega*t)`, K/R notation unless the task explicitly
states another convention.

## Reference routing

- To choose or derive a continuous SIE, or to work with the thesis waveguide
  port system: read `references/SIE_FORMULATIONS.md`.
- For PWC/collocation versus RWG/Galerkin discretization:
  read `references/SURFACE_DISCRETIZATION.md`.
- For PEC/dielectric contacts, open-sheet sides, or multi-region junction
  topology: read `references/SURFACE_JUNCTIONS.md`.
- If source signs/trace conventions differ from the project:
  use the `electromagnetics-notation` skill.

Do not load junction rules for an ordinary smooth closed scatterer.
