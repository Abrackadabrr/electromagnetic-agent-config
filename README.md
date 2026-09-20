# electromagnetic-agent-config

Shared Codex skills for research and software development in computational
electromagnetics based on integral equations.

The configuration is intentionally focused on:

- surface integral equations (SIE);
- volume integral equations (VIE);
- coupled surface-volume formulations (VSIE);
- discretization and singular integration of electromagnetic operators;
- structured electromagnetic problems: repeated/periodic geometry,
  translation-invariant interaction blocks, low-rank separated interactions,
  and regular-grid voxel operators.

FEM / FE-BI is intentionally outside the current scope.

## Canonical notation

The canonical convention follows the author's thesis and must be preserved
throughout the skills:

- time dependence: `exp(-i*omega*t)`;
- Maxwell:
  `curl E = +i*omega*epsilon*H`,
  `curl H = -i*omega*mu*E` in the source-free homogeneous exterior;
- outgoing scalar Green function:
  `F(x-y) = exp(+i*k*|x-y|)/(4*pi*|x-y|)`;
- project operators:
  `K[Q,j] = grad div int_Q j(y)F(x-y)dQ_y + k^2 int_Q j(y)F(x-y)dQ_y`,
  `R[Q,j] = int_Q grad_x F(x-y) cross j(y)dQ_y`.

When importing literature using another harmonic convention, convert the whole
convention bundle before reusing equations.

## Codex layout

This repository is meant to be exposed directly under `.agents/skills`.
Each top-level skill directory contains a focused `SKILL.md`; detailed
mathematics lives in `references/` and should be loaded only when relevant.

Current skills:

- `electromagnetics-notation`;
- `surface-integral-equations`;
- `volume-integral-equations`;
- `operator-discretization`;
- `uniform-grid-vie`;
- `structured-em-operators`.

Repository/project-specific API maps do **not** belong here. Put them in the
consuming repository's `AGENTS.md`, docs, or a project-local skill.

## Research direction

The thesis baseline is not only a notation source. It defines the intended
research direction: exploit structure created by integral-equation
discretizations. Important examples are repeated interaction blocks in
periodic arrays, block/multilevel Toeplitz structure, low-rank far
interactions, regular-grid VIE translation invariance, and preconditioners or
tensor representations that preserve these structures.

For generic Toeplitz/FFT/BLAS/LAPACK/preconditioning implementation details,
use a numerical-linear-algebra skill set rather than duplicating those topics
inside this repository.
