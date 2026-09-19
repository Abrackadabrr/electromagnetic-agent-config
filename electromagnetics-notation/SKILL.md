---
name: electromagnetics-notation
description: Canonical sign, harmonic-time, Green-function, and K/R operator notation for this project's electromagnetic integral-equation code.
---

# Electromagnetics Notation

## Response language

Respond to the user primarily in Russian. Mixed Russian-English technical prose is explicitly allowed when translation could change, narrow, or obscure meaning. Do not translate mathematical symbols, operator names, function-space names, established computational-electromagnetics terminology, source-code identifiers, API names, or source notation merely to make the prose fully Russian.

Load this skill before any EM derivation or implementation.

## Canonical convention

Use `exp(-i*omega*t)` throughout.

Therefore, in a homogeneous source-free isotropic region:

`curl E = +i*omega*mu*H`

`curl H = -i*omega*epsilon*E`

and the outgoing scalar Green function is

`G_k(x,y) = exp(+i*k*R)/(4*pi*R)`, `R = |x-y|`.

Never import a formula containing `exp(-ikR)` without translating the complete
harmonic convention.

## Canonical operators

Project notation:

`K_user <-> k^2 L_Gibson`

`R_user <-> K_Gibson`

after convention translation.

Read `references/ELECTROMAGNETICS_NOTATION.md` for canonical formulas and
`references/NOTATION_TRANSLATION.md` before using Gibson or another source with
an opposite harmonic convention.

## Repository-specific warning

In the EMW codebase, `Helmholtz::V` is documented as minus `grad_x G`. Expand it
before reasoning about `R` signs. The C++ identifier is not the mathematical
operator definition.
