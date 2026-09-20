---
name: uniform-grid-vie
description: Explain and discretize electromagnetic VIEs on uniform Cartesian voxel grids, including when the Green interaction is translation-invariant/block-Toeplitz and how material terms break full Toeplitz structure. Use for EM-specific voxel/operator structure; use NLA skills for generic FFT/circulant implementation.
---

# Uniform-grid VIE

Assume the project harmonic convention and a homogeneous background Green
operator.

## Core fact

For identical translated voxels with translated basis/testing functions, the
background Green interaction depends only on the relative voxel displacement.

That is the electromagnetic reason a regular-grid interaction operator admits
multilevel block-Toeplitz representation.

The spatially varying material multiplier is local and generally destroys
Toeplitz structure of the complete heterogeneous VIE if it is fused into the
convolution matrix. Keep the material map separate.

## Reference routing

- For PWC/PWL voxel Galerkin structure:
  read `references/VOXEL_GALERKIN.md`.
- For exact conditions under which translation invariance holds:
  read `references/TRANSLATION_INVARIANCE.md`.
- For generic Toeplitz/circulant/FFT layout and optimization:
  use the NLA `structured-matrices`, `linear-algebra-backends`, and
  `performance-engineering` skills when available.

Do not duplicate generic FFT implementation advice in this EM skill.
