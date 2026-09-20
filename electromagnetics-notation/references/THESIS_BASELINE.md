# Author-thesis baseline

This file records the conventions and numerical baseline that future work
should preserve, while explicitly marking internal inconsistencies in the
printed thesis that must not be propagated blindly.

## Time convention

The thesis uses

`E_hat(x,t)=E(x) exp(-i*omega*t)`,
`H_hat(x,t)=H(x) exp(-i*omega*t)`.

The outgoing condition and Green function are consistent with `exp(+ikr)`.

## Maxwell-equation audit

The printed thesis Eq. (1) shows

`rot E = +i*epsilon*omega*H`,
`rot H = -i*mu*omega*E`,

while the surrounding text identifies epsilon as dielectric permittivity and mu
as magnetic permeability.

With those standard SI material meanings and the same `exp(-i*omega*t)`
convention, the physically consistent source-free equations are

`curl E = +i*omega*mu*H`,
`curl H = -i*omega*epsilon*E`.

Later field representations in the thesis are consistent with the standard
material roles rather than with blindly swapping epsilon/mu.

Therefore:

- preserve the thesis harmonic sign convention;
- preserve its K/R and Green-function notation;
- do **not** propagate the printed epsilon/mu swap as a project convention;
- when a derivation depends on Maxwell prefactors, re-derive it from the
  standard SI equations above.

## Surface orientation and traces

For closed PEC components, `n` is the outward normal. On an open surface,
positive side/orientation is chosen consistently and the PEC tangential
condition is imposed on both sides.

The thesis denotes boundary values with:

- minus trace: exterior side;
- plus trace: interior side.

Keep that convention when quoting its jump formulas.

## Scalar Green function

`F(x-y) = exp(+i*k*|x-y|)/(4*pi*|x-y|)`.

## Project K and R

For a tangential surface field `j`:

`K[Sigma,j](x)
 = grad_x div_x int_Sigma j(y) F(x-y) dS_y
 + k^2 int_Sigma j(y) F(x-y) dS_y`.

`R[Sigma,j](x)
 = int_Sigma grad_x F(x-y) cross j(y) dS_y`.

The thesis states, at smooth non-edge points:

`R^+ = R + 1/2 (j cross n)`,
`R^- = R - 1/2 (j cross n)`.

It also states:

`K^+ = K - 1/2 n Div_S j`,
`K^- = K + 1/2 n Div_S j`.

Do not reuse these signs under another normal or plus/minus convention without
translation.

## Field representation used in the thesis

With electric surface-current density `j_E` on `Sigma` and magnetic
surface-current density `j_M` on the waveguide-port surface `Sigma_0`:

`E = i/(omega*epsilon_0) K[Sigma,j_E] - R[Sigma_0,j_M]`.

`H = R[Sigma,j_E] + i/(omega*mu_0) K[Sigma_0,j_M]`.

These current definitions are the baseline for the waveguide-port formulation;
do not silently replace them by another equivalence-principle convention.

## Printed Eq. (13) audit warning

In the thesis, the third equation of the algebraically transformed system
(Eq. 13) prints a coefficient `i Z/(omega epsilon_0)` multiplying
`K[Sigma_0,j_M]`.

Eq. (12), however, contains `i/(omega mu_0) K[Sigma_0,j_M]`; direct
substitution into the impedance boundary condition therefore requires an
explicit audit before reusing Eq. (13).

Do **not** silently “correct” or blindly copy this term. Re-derive the
coefficient from Eqs. (4), (5), (11), and (12), and compare with existing
project code/tests.

## Thesis discretization baseline

The surface is approximated by conforming quadrilateral cells `sigma_k`.
Each cell has:

- collocation point `x_k`;
- approximate normal `n_k`;
- local right-handed orthonormal frame `{e_1,k, e_2,k, n_k}`;
- piecewise-constant tangential current coefficients.

The currents are represented as

`j_k = j_k^1 e_1,k + j_k^2 e_2,k`.

The thesis collocation matrix coefficients are projected with the bilinear
complex dot product

`<x,y> = x_1 y_1 + x_2 y_2 + x_3 y_3`

(without complex conjugation). Do not silently replace it by a Hermitian inner
product.

## Thesis singular-integration baseline

For K:

- regular/far cells may differentiate under the integral and use ordinary
  Gaussian quadrature;
- self and sufficiently near interactions split `K=K_0+K_1`;
- `K_1=k^2 j int F` uses analytic extraction of the `1/R` singularity plus
  quadrature for the bounded remainder;
- for constant PWC current, `K_0` is transformed to a contour/edge integral.

For R:

- distinct cells use a regular integral;
- for a planar self cell with constant tangential current, the direct self
  value in this scheme is zero.

## Structured-matrix baseline

For repeated translated elements, matrix blocks are interpreted as receiver
element I versus source element J interactions. Equal relative placements give
equal interaction blocks.

For a rectangular `M1 x M2` array, the thesis obtains a two-level
block-Toeplitz structure with `(2*M1-1)(2*M2-1)` distinct interaction blocks
instead of `(M1*M2)^2`.

Separated off-diagonal interaction blocks are treated as numerically low rank
and approximated by ACA. The thesis solves with GMRES and uses a block-diagonal
preconditioner made from the equal diagonal self-interaction blocks.

The thesis implementation also batches repeated applications of the same dense
interaction block into matrix-matrix products so BLAS-3 kernels can be used.

## Intended continuation

The thesis explicitly identifies improved preconditioning as a future need and
discusses tensor/QTT ideas and regular-grid VIE matrices as natural extensions.
Future research should preserve this theme: exploit physical translation
invariance, repeated blocks, numerical low rank, and structured inverse or
preconditioner representations instead of materializing generic dense matrices.
