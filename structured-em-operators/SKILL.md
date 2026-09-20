---
name: structured-em-operators
description: Identify and exploit matrix structure caused by repeated or separated electromagnetic integral-equation geometry: repeated interaction blocks, multilevel block-Toeplitz structure, low-rank far blocks, and structure-preserving Krylov/preconditioning research. Use for EM-specific structure discovery; use NLA skills for generic implementation kernels.
---

# Structured electromagnetic operators

This skill follows the central research direction of the author's thesis:
derive matrix structure from geometry and the integral kernel before choosing a
linear-algebra representation.

## Reference routing

- For repeated/periodic elements and block-Toeplitz structure:
  read `references/PERIODIC_BLOCK_STRUCTURE.md`.
- For separated interactions and ACA/low-rank reasoning:
  read `references/LOW_RANK_INTERACTIONS.md`.
- For solver/preconditioner/tensor research directions:
  read `references/RESEARCH_ROADMAP.md`.

Do not materialize a generic dense matrix until the geometric invariances and
separation structure have been checked.
