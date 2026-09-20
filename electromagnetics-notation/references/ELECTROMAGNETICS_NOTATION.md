# Canonical electromagnetic notation

## Homogeneous source-free medium

Under `exp(-i*omega*t)`:

`curl E = +i*omega*mu*H`,
`curl H = -i*omega*epsilon*E`,
`k=omega*sqrt(epsilon*mu)`.

For source-free homogeneous regions both fields satisfy the vector Helmholtz
equation.

## Green function

`R=|x-y|`,
`F_k(x-y)=exp(+i*k*R)/(4*pi*R)`.

Away from `x=y`:

`grad_x F_k = -grad_y F_k`.

## Generic project K operator

For a surface or volume source domain Q:

`K[Q,j](x)
 = grad_x div_x int_Q F_k(x-y) j(y) dQ_y
 + k^2 int_Q F_k(x-y) j(y) dQ_y`.

When Q contains x, interpret/discretize this operator through the formulation's
valid weak, finite-part, singularity-extracted, or distributional form. Do not
numerically evaluate a coincident Hessian-like kernel by ordinary quadrature.

## Generic project R operator

`R[Q,j](x)=int_Q grad_x F_k(x-y) cross j(y) dQ_y`.

Cross-product order is part of the definition.

## Electric-current field map

For an electric current density J radiating in a homogeneous background:

`E_J = i/(omega*epsilon) K[J]`,
`H_J = R[J]`,

provided J uses the same physical/current convention as this representation.

A magnetic-current contribution must be derived from the declared magnetic
current convention rather than guessed from operator names.

## Gibson symbol map

After full convention translation:

- project `K` corresponds to `k^2 L_Gibson`;
- project `R` corresponds to `K_Gibson`.

This is a notation map, not permission to copy Gibson signs verbatim.
