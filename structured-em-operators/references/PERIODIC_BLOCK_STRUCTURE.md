# Repeated geometry and block-Toeplitz structure

## Thesis baseline

The thesis considers a system of identical electromagnetic elements obtained
by translations of one base element, with each element carrying an identically
translated discretization.

A matrix block `A_IJ` maps source unknowns on element J to receiver equations
on element I.

If a rigid translation maps the pair `(I,J)` to `(I',J')` while preserving
the local discretization and orientation, then the corresponding interaction
blocks are equal:

`A_IJ = A_I'J'`.

For a rectangular `M1 x M2` array of translated elements, this produces a
two-level block-Toeplitz pattern.

The number of pair blocks in a full dense block matrix is
`(M1*M2)^2`, while only

`(2*M1-1)(2*M2-1)`

relative-displacement blocks are distinct.

## Implementation contract

Before using block reuse, record:

- receiver element index;
- source element index;
- displacement map;
- local DOF ordering inside every element;
- local basis orientation;
- whether diagonal/nonintegral terms are displacement-invariant;
- whether a rotation/reflection as well as translation is involved.

Do not use modulo indexing to turn a Toeplitz operator into a circulant
operator unless periodic wrap-around is physically intended or is only an FFT
embedding device.

## Generalization

The same idea applies beyond waveguide arrays:

- periodic or repeated PEC scatterers;
- repeated dielectric inclusions;
- repeated SIE/VSIE unit cells;
- regular voxel grids (at the voxel interaction level).

The physical source is translation invariance of the homogeneous-background
integral kernel together with translated discretizations.
