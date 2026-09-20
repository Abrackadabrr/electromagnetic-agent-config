# Convention audit template

Use this template when a source, derivation, and implementation disagree.

## Source convention

- time factor:
- scalar Green function:
- outgoing phase:
- Maxwell curl E:
- Maxwell curl H:
- electric-current definition:
- magnetic-current definition:
- normal direction:
- plus trace means:
- minus trace means:
- gradient variable:
- cross-product order:
- source operator names:

## Project target

- time factor: `exp(-i*omega*t)`
- Green: `exp(+ikR)/(4*pi*R)`
- project K:
- project R:
- current definitions used by this task:
- normal:
- trace side needed:

## Translation steps

1. Re-derive source terms from Maxwell under the target time factor.
2. Replace the Green function and all derivatives consistently.
3. Convert current definitions.
4. Convert normal and trace-side conventions.
5. Expand cross products before changing their order.
6. Convert jump terms.
7. Rename operators into project K/R notation only now.
8. Derive the matrix coefficient from the translated continuous equation.
9. Add a sign/normalization regression test before deleting the old path.

## Sanity checks

- far field has the intended outgoing phase;
- `grad_x F=-grad_y F`;
- units of every field contribution match;
- swapping a cross product changes sign;
- a simple symmetry/analytic case agrees with an independent result.
