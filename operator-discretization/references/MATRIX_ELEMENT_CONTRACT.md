# Matrix-element contract

Fill this before implementing or changing an EM operator matrix.

## Continuous layer

- equation:
- operator:
- source domain:
- observation/test domain:
- unknown definition:
- units/normalization:

## Discrete layer

- row index represents:
- column index represents:
- source cell/basis:
- receiver/test cell/basis:
- source orientation:
- receiver orientation:
- basis support:
- test support:
- pairing: collocation / bilinear / sesquilinear Galerkin:
- complex conjugation: yes/no:
- component ordering:
- flattening/permutation:

## Interaction layer

- self definition:
- adjacent/near definition:
- far definition:
- self treatment:
- near treatment:
- far quadrature:
- jump/direct-value term:
- singularity convention:

## Validation

- tiny hand-checkable geometry:
- independent/reference implementation:
- analytic limit if available:
- expected symmetry/reciprocity (only if mathematically valid):
- units:
- tolerance:

## Thesis baseline example

For PWC surface collocation:

- row: receiver cell k + receiver tangent component p;
- column: source cell j + source tangent component m;
- source: constant `e_m,j` on `sigma_j`;
- test: projection onto `e_p,k` at `x_k`;
- pairing: bilinear complex dot product, no conjugation.
