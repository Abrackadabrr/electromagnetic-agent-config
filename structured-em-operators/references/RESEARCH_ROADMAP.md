# Structured-EM research roadmap

The thesis establishes a useful baseline:

- block/multilevel Toeplitz structure from repeated translated geometry;
- low-rank approximation of separated interaction blocks;
- GMRES with matrix-free/block structured matvec;
- block-diagonal preconditioning using the repeated diagonal self block;
- BLAS-3 batching when the same interaction block acts on many vector blocks.

It also identifies improved preconditioning and tensor/QTT representations as
future directions, with regular-grid VIE as another structured electromagnetic
setting.

## Recommended research ladder

### 1. Preserve exact physical structure

Establish which matrix components are exactly repeated/Toeplitz and which are
only approximately low rank.

### 2. Separate exact structure from approximation

Keep:

- exact diagonal/self blocks;
- exact displacement reuse where valid;
- low-rank approximations only for selected separated interactions.

Measure approximation error per block and on the global operator.

### 3. Study solver consequences

For every compression/structured approximation report:

- matvec error;
- spectrum/field-of-values indicators when useful;
- GMRES iterations/restarts;
- true residual;
- physical observable error;
- setup, memory, and solve time.

### 4. Preconditioning

Candidate hierarchy:

- repeated block-diagonal self-block preconditioner;
- block lower-triangular approximations;
- circulant/multilevel circulant approximations of Toeplitz interaction
  structure;
- sparse/ILU approximations only after defining a sparse surrogate;
- low-rank/tensor approximate inverses.

Generic construction algorithms belong to NLA skills.

### 5. Regular-grid VIE

Use voxel translation invariance to expose multilevel block-Toeplitz Green
operators. Keep heterogeneous material terms local. Compare direct structured
matvec, FFT matvec, and structured preconditioners.

### 6. Tensor/QTT direction

Treat tensorization as a representation hypothesis to be tested, not an
automatic improvement. Measure tensor ranks against frequency, electrical
size, geometry, material contrast, and requested tolerance.

Compare tensor solvers/preconditioners with classical Krylov + structured
matvec at equal accuracy.
