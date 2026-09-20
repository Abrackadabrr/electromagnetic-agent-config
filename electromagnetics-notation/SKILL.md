---
name: electromagnetics-notation
description: Translate or audit EM formulas involving time-harmonic signs, outgoing Green functions, K/R operators, trace sides, normals, current definitions, or cross-product order. Use for sign/normalization derivations; do not trigger for ordinary code changes with no electromagnetic formula.
---

# Electromagnetics notation

Use the author's thesis convention as the default:

`exp(-i*omega*t)`, `F=exp(+ikR)/(4*pi*R)`.

Do not convert only the exponential sign. Treat the time factor, Maxwell curl
signs, Green function, current definitions, normal/trace side, operator
prefactors, jump terms, and cross-product order as one convention bundle.

## Reference routing

- For the exact canonical convention and thesis baseline:
  read `references/THESIS_BASELINE.md`.
- For reusable operator formulas:
  read `references/ELECTROMAGNETICS_NOTATION.md`.
- When importing Gibson or any source with a different convention:
  read `references/NOTATION_TRANSLATION.md`.
- When a sign disagreement is being debugged:
  fill `references/CONVENTION_AUDIT.md` before changing code.

Do not infer a mathematical sign from a C++ helper name.
