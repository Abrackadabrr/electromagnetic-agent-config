# Discretization patterns

## PWC collocation

A coefficient is an operator value at a receiver point projected onto a local
receiver direction. It is not an L2 Galerkin integral.

Use the thesis matrix-entry convention when working on the baseline EMW-style
surface scheme.

## RWG Galerkin

RWG functions are edge-based surface basis functions on triangle pairs.
Preserve edge orientation consistently in basis, surface divergence, and
testing.

Do not treat an RWG coefficient as a point-sampled PWC coefficient.

## SWG / tetrahedral volume basis

SWG-type functions are classical divergence-conforming volume bases associated
with tetrahedral faces. Their continuity and normalization must match the
chosen VIE unknown, especially D-VIE/flux-density formulations.

## Cartesian PWC/PWL volume basis

On a regular voxel grid, translated basis/testing functions should be generated
from one reference voxel whenever translation invariance is being exploited.

PWC vector basis: typically three Cartesian component coefficients per voxel.

Discontinuous PWL: local scalar pulse/linear modes times vector components;
self/near formulas must be re-derived rather than copied from PWC.

## Mixed VSIE blocks

A surface-to-volume block and a volume-to-surface block can use different
source and test spaces. Derive each block from the physical field
representation. Do not create one generic matrix-entry template that assumes
same-dimensional cells on both sides.
