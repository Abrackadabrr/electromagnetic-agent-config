# Translation invariance in regular-grid electromagnetic VIE

Let source voxel q and receiver voxel p be translations of a fixed reference
voxel. Let their basis/test functions also be translations of fixed reference
functions.

In a homogeneous background,

`F_b(x,y)=F_b(x-y)`.

After translating both source and receiver integration variables by the same
grid vector, a Galerkin/collocation interaction coefficient depends only on

`delta = index(receiver)-index(source)`.

Therefore

`A_{p,q}=B_delta`

for the homogeneous-background interaction operator.

## Required conditions

Exact displacement reuse requires:

- homogeneous background Green function;
- congruent translated cells;
- identically translated basis/test functions;
- consistent component orientation;
- identical quadrature/singularity treatment for geometrically equivalent
  pairs;
- no source/receiver-dependent material coefficient folded into the kernel.

## What can break it

- nonuniform voxel sizes;
- rotated local bases;
- boundaries represented by modified cell shapes;
- spatially varying background medium;
- source-dependent quadrature rules not invariant under translation;
- material contrast multiplied into and stored as part of the interaction
  coefficient.

## Vector block structure

With three Cartesian PWC components, each displacement stores a small 3x3
interaction block. The large operator is therefore a multilevel Toeplitz
operator with small dense physical-component blocks.

The generic storage, circulant embedding, FFT batching, and block-frequency
multiplication are NLA concerns and should be delegated to the corresponding
skills.
