---
name: operator-discretization
description: Translate a continuous EM integral operator into matrix coefficients, quadrature, singular/self/near treatment, basis/testing conventions, and indexing/orientation contracts. Use for assembly or operator implementation; do not trigger for formulation-only questions with no discretization.
---

# Operator discretization

Before writing assembly code, make the mathematical matrix-entry contract
explicit.

## Reference routing

- For the required row/column/source/test contract:
  read `references/MATRIX_ELEMENT_CONTRACT.md`.
- For collocation, Galerkin, RWG, SWG, PWC, and Cartesian basis patterns:
  read `references/DISCRETIZATION_PATTERNS.md`.
- For self/near/far classification and singularity extraction:
  read `references/QUADRATURE_AND_SINGULARITIES.md`.
- For project sign conventions use `electromagnetics-notation` only when
  signs, traces, or operator definitions are actually involved.
