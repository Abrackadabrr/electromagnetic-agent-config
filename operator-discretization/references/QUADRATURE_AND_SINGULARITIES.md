# Quadrature and Singularities

## Interaction classification

Do not use one quadrature rule for all pairs. Classify at least:

- far regular;
- near regular but sharply varying;
- touching/adjacent;
- self/coincident;
- principal-value or finite-part cases where required by the operator.

## Singularity extraction

For `G=exp(+ikR)/(4*pi*R)`, a basic split is

`G = 1/(4*pi*R) + [exp(+ikR)-1]/(4*pi*R)`.

The bracketed term is bounded as `R -> 0`. Integrate the Newtonian-potential part
analytically when an appropriate cell formula exists, and integrate the bounded
remainder numerically.

## Project surface PWC K

The thesis/code path splits K into:

- a `grad div` contribution that can be transformed to cell-boundary/contour
  integrals for PWC cells;
- a `k^2` Green-potential contribution with `1/R` singularity extraction.

Near non-self cells may require the same stabilized path even when the integral
is formally regular.

## Project voxel PWC K

The current volume code uses a useful weak/distributional structure:

- `k^2 * int_V G j` is evaluated as a volume potential;
- the `grad div` contribution of a cellwise constant vector field is represented
  by jumps of normal/component values across voxel faces and surface integrals.

This avoids direct coincident evaluation of a Hessian-like kernel. Preserve this
strategy unless replacing it with a mathematically derived alternative.

## Error control

Adaptive integration tolerances are numerical parameters, not physical
constants. Convergence studies must vary quadrature/refinement independently of
mesh resolution.
