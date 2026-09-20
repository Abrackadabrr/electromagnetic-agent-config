# Translation from external electromagnetic conventions

## Required translation record

Before copying a formula, record:

1. time factor;
2. outgoing Green function;
3. Maxwell curl signs;
4. electric-current definition;
5. magnetic-current definition;
6. normal orientation;
7. meaning of plus/minus traces;
8. gradient variable (x or y);
9. cross-product order;
10. operator names and prefactors.

Only then rename the source operators into project K/R notation.

## Gibson-to-project baseline

Gibson commonly uses the opposite harmonic convention and
`exp(-ikR)/(4*pi*R)` outgoing phase.

The project uses `exp(-i*omega*t)` and
`exp(+ikR)/(4*pi*R)`.

After the whole convention is translated:

- `K_project = k^2 L_Gibson`;
- `R_project = K_Gibson`.

## Do not use blind complex conjugation

For real lossless coefficients, changing harmonic convention can resemble
complex conjugation. This is not a safe general algorithm for lossy media,
complex material coefficients, branch-dependent square roots, impressed
currents, or mixed normal/trace conventions.

Re-derive prefactors from Maxwell equations.

## Minimal derivative checks

Always verify:

`grad_x F = -grad_y F`.

For code helpers returning `-grad_x F`, expand the sign before applying a
cross product.

## Jump-term checks

A jump formula is meaningful only together with:

- chosen normal;
- source side;
- plus/minus definition;
- trace operator;
- current orientation.

Never transport only the `1/2` term between formulations.
