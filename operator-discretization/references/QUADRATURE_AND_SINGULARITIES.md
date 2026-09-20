# Quadrature and singularities

## Interaction classes

At minimum distinguish:

- far regular;
- near regular but rapidly varying;
- touching/adjacent;
- coincident/self;
- principal-value or finite-part cases when required by the operator.

## Helmholtz singularity extraction

With project Green function:

`F=1/(4*pi*R) + [exp(i*k*R)-1]/(4*pi*R)`.

The bracketed term is bounded as `R -> 0`.

When an analytic cell formula is available, integrate the Newtonian part
analytically and use numerical quadrature only on the bounded remainder.

## Thesis surface-PWC K path

- far: differentiated regular kernel + Gaussian quadrature;
- self/near: split `K=K_0+K_1`;
- `K_1`: analytic `1/R` extraction;
- `K_0`: contour/edge reduction for constant PWC current.

## Volume-PWC principle

For a cellwise-constant volume field, a weak/distributional treatment can move
the grad-div contribution onto voxel faces/jumps instead of numerically
evaluating a coincident Hessian kernel.

## Error control

Quadrature order, near threshold, and adaptive tolerance are numerical
parameters. Validate them independently of the physical mesh-refinement study.

Never justify a singular rule only because a final linear solve “looks
reasonable.”
