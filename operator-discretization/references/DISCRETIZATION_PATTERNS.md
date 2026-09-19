# Discretization Patterns

## Collocation/PWC

A matrix coefficient is an operator value at a collocation point projected onto
a local testing direction. It is not an L2 Galerkin inner product.

## Galerkin

A matrix coefficient is a tested integral of an operator applied to a source
basis. Keep complex inner-product convention explicit: bilinear versus
sesquilinear testing must match the project implementation.

## Surface RWG

RWG basis functions live on triangle pairs and encode normal-current continuity
across the common edge. Use signed edge orientation consistently in basis,
divergence, and testing.

## Volume SWG

SWG functions live on tetrahedral face neighborhoods and are commonly used for
divergence-conforming volume discretizations. Their continuity and normalization
must match the selected VIE unknown.

## Cartesian PWC/PWL

For translated voxels on a uniform grid, choose one fixed local scalar/vector
basis on the reference voxel and obtain every other basis by translation. This
is the algebraic prerequisite for exact displacement-based Toeplitz storage of
the homogeneous-background Green operator.

## Cross-discretization blocks

In VSIE, a surface-to-volume block and a volume-to-surface block may use
different basis/test spaces and dimensions. Derive each tested integral directly
rather than forcing a shared matrix-element template that assumes identical
cell dimensionality.
