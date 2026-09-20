# Surface discretization

## Thesis PWC collocation path

The thesis baseline uses quadrilateral cells with one collocation point per
cell and a local right-handed orthonormal frame
`{e_1,k,e_2,k,n_k}`.

A tangential PWC current is represented by two coefficients per cell:

`j_k=j_k^1 e_1,k+j_k^2 e_2,k`.

A matrix entry is an operator value at receiver collocation point `x_k`,
projected onto receiver direction `e_p,k`, for a source cell `sigma_j` and
source direction `e_m,j`.

For example:

`a_kj^{pm}=< K_tilde[sigma_j,e_m,j](x_k), e_p,k >`;

`b_kj^{pm}=< R_tilde[sigma_j,e_m,j](x_k), e_p,k >`.

The thesis uses a bilinear complex dot product without conjugation. Preserve
that unless a new Galerkin formulation explicitly defines a sesquilinear
pairing.

## PWC K interactions

Classify receiver/source cells before quadrature.

### Far regular

For sufficiently separated cells, differentiate under the integral and use a
regular quadrature.

### Self / near

Use the thesis split:

`K=K_0+K_1`.

- `K_1=k^2 j int F dS`: extract the `1/R` singularity analytically and
  quadrature the bounded remainder.
- `K_0=grad div int j F dS`: for constant PWC current, transform to the
  contour/edge representation used by the thesis.

Near-but-disjoint cells may still require the stabilized self/near path.

## PWC R interactions

Distinct cells use a regular integral. For a planar self cell and constant
tangential source current, the direct value in the thesis scheme is zero.

## RWG/Galerkin path

RWG is a separate discretization family:

- triangular mesh;
- divergence-conforming edge basis;
- source and test functions have two-triangle support;
- matrix coefficients are tested integrals, not collocation projections.

Classify triangle pairs as far, near, vertex adjacent, edge adjacent, and
coincident before selecting quadrature.

Do not reuse PWC self terms or matrix normalization in an RWG implementation.

## Required ordering record

Before coding, document:

- global cell/edge ordering;
- component ordering;
- source-column meaning;
- receiver-row meaning;
- local orientation signs;
- whether test pairing is bilinear or sesquilinear.
