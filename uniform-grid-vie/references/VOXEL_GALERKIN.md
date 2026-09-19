# Voxel Galerkin Discretization

## PWC

With a vector PWC basis there are three Cartesian component coefficients per
voxel. For a homogeneous grid the interaction between two voxels is a `3 x 3`
block indexed by their relative displacement.

The current EMW volume-K implementation is Galerkin-oriented and separates a
surface/face contribution from a scalar volume Green contribution. Near and
self interactions use singularity extraction and analytic Newtonian-potential
terms; far interactions may use a direct smooth kernel.

## PWL

Discontinuous PWL voxel schemes add local linear scalar modes. A common
construction has four scalar modes per voxel (pulse plus x/y/z slopes) times
three vector components, giving 12 coefficients per voxel. Do not assume the PWC
self/near formulas carry over unchanged.

## Material contrast

If solving a current-based formulation, keep the local constitutive relation as
a diagonal or small block-diagonal voxel operator when possible. This lets the
translation-invariant Green operator remain separately FFT-accelerable.

## Masked geometry

A complex shape can be embedded in a rectangular voxel bounding grid with
inactive entries masked or zeroed. The FFT convolution acts on the embedding;
the physical unknown/update logic controls active material cells.
