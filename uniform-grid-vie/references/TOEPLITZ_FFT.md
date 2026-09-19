# 3-D Toeplitz and FFT Matvec

## Displacement tensor

For grid sizes `(Nx,Ny,Nz)`, store interaction blocks for relative offsets

`dx in [-(Nx-1), Nx-1]`,
`dy in [-(Ny-1), Ny-1]`,
`dz in [-(Nz-1), Nz-1]`.

For vector PWC, each displacement carries a `3 x 3` block.

## Circulant embedding

A Toeplitz matvec can be embedded in a 3-D circular convolution. Zero-pad enough
to contain the linear convolution support; logical dimensions of at least
`(2*Nx-1, 2*Ny-1, 2*Nz-1)` are sufficient before any implementation-specific
rounding to FFT-friendly sizes.

Carefully map negative offsets into the wrapped circulant indices. A single sign
or permutation error can produce plausible but wrong fields.

## Precomputation

For repeated iterative matvecs:

1. build the displacement kernel once;
2. create the circulant embedding;
3. FFT each independent kernel component/block channel once;
4. on each matvec, FFT source component arrays, multiply/couple in Fourier
   space, inverse FFT, crop, and apply physical masks/material terms.

## Validation

Before benchmarking, compare on a small grid:

- dense matrix assembled from the same cell integrals;
- explicit Toeplitz matvec;
- FFT matvec.

Use random complex vectors and report relative 2-norm error. Test all component
channels and several non-cubic grid sizes to expose indexing mistakes.
