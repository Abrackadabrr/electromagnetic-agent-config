# Translation from External Electromagnetic Conventions

## Gibson-to-project symbol map

Gibson commonly uses `exp(+i*omega*t)` and outgoing
`exp(-ikR)/(4*pi*R)`.

This project uses `exp(-i*omega*t)` and outgoing
`exp(+ikR)/(4*pi*R)`.

After translating the harmonic convention:

- project `K` corresponds to `k^2 * Gibson L`;
- project `R` corresponds to `Gibson K`.

The mapping is semantic, not a copy/paste identity.

## Required conversion procedure

When importing an equation:

1. record the source time factor;
2. record the source Green function and outgoing branch;
3. record Maxwell curl signs;
4. record source definitions of `J` and `M`;
5. record normal direction and trace-side definitions;
6. record cross-product order;
7. derive the same physical field in project convention;
8. rename operators only after steps 1-7.

## Do not use blind conjugation

For real lossless parameters many formulas look like complex conjugates after a
harmonic-convention swap. This shortcut is unsafe for lossy/complex media and
branch-dependent square roots. Derive signs from Maxwell equations instead.

## Common failure mode

Changing `exp(-ikR)` to `exp(+ikR)` while retaining Gibson's `-i*omega`
prefactors produces an inconsistent solver. Treat time, Green function,
operator prefactors, jump relations, and far-field phase as one convention
bundle.
