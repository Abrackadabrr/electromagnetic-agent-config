---
name: operator-discretization
description: Matrix-element derivation, Galerkin/collocation assembly, singular and near-singular quadrature, and validation for EM integral operators.
---

# Operator Discretization

Always load `electromagnetics-notation` first.

## Required assembly record

For every matrix coefficient state:

- continuous operator;
- source/test domains;
- basis/test functions;
- local/global orientation;
- exact normalization;
- geometry interaction class;
- singularity treatment;
- quadrature order/adaptivity;
- expected units and symmetry/reciprocity properties.

Read:

- `references/QUADRATURE_AND_SINGULARITIES.md`;
- `references/DISCRETIZATION_PATTERNS.md`.
