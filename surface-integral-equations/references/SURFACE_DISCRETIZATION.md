# Surface Discretization

## Project/thesis PWC collocation path

A surface is split into quadrilateral/parallelogram cells. On each cell choose a
collocation point and a local right-handed orthonormal frame
`{e1, e2, n}`. A tangential current is approximated as

`j|cell = j1*e1 + j2*e2`.

Operator equations are enforced at collocation points and projected onto `e1`
and `e2`.

For project `K`:

- far interactions may move derivatives under the integral and use standard
  Gaussian quadrature;
- self and sufficiently near interactions use a split into `grad div` and
  `k^2` parts;
- the `1/R` singularity in the Green term is extracted, with an analytic
  potential integral plus a smooth remainder;
- the `grad div` part may be transformed to contour/edge integrals for PWC
  cells.

For project `R`, preserve the exact `grad_x G cross j` order and check the
repository's `Helmholtz::V=-grad_x G` helper before using it.

## RWG Galerkin path

For a triangular surface mesh, RWG functions are divergence-conforming surface
basis functions supported on adjacent triangle pairs. Use them only when the
task explicitly selects the RWG/Galerkin formulation or when an existing code
path already uses it.

For each tested source pair classify: disjoint far, disjoint near, edge-adjacent,
vertex-adjacent, coincident/overlap. Use a quadrature strategy appropriate to
that class.

## Never mix PWC and RWG matrix formulas

A PWC collocation self term and an RWG Galerkin self term have different
mathematical objects and singularity reductions. Reusing code solely because
both are called `K` is an error.
