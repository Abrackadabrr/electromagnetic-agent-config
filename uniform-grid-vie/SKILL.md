---
name: uniform-grid-vie
description: Regular Cartesian voxel VIE discretization, block-Toeplitz structure, FFT convolution, and mapping to the EMW codebase.
---

# Uniform-Grid VIE

Also load `electromagnetics-notation`, `volume-integral-equations`, and
`operator-discretization`.

## Core invariance

For a homogeneous background, identical translated voxels, and translated
basis/testing functions, the Green interaction depends only on voxel-index
displacement. Encode the Green block as a 3-D block-Toeplitz operator.

Do not claim the full inhomogeneous VIE matrix is Toeplitz if spatially varying
material contrast is multiplied into it. Keep convolution and material-local
operators separate.

Read:

- `references/VOXEL_GALERKIN.md`;
- `references/TOEPLITZ_FFT.md`;
- `references/EMW_CODEBASE_MAPPING.md`.
