# Low-rank separated electromagnetic interactions

For two well-separated source/receiver groups, the Green kernel and its
relevant derivatives are smooth on the Cartesian product of the two groups.

After discretization, this often produces rapidly decaying singular values in
the interaction block.

## Thesis baseline

The thesis approximates separated off-diagonal interaction blocks as

`A ~= U V^*`

using adaptive cross approximation (ACA), avoiding construction of every
matrix entry.

Applying the block becomes

`A x ~= U (V^* x)`.

The approximation tolerance controls both memory and matvec work.

## Before applying low rank

1. define the physical source and receiver groups;
2. identify whether they overlap/touch;
3. inspect or estimate singular-value decay versus separation;
4. choose an approximation norm/tolerance;
5. validate the block approximation independently from the global solve;
6. measure how approximation changes Krylov convergence as well as matvec
   cost.

A low matrix-approximation error does not automatically imply unchanged solver
iterations or unchanged physical observables.

## ACA implementation boundary

The EM skill explains *why* separation produces low rank and what error must be
validated. Generic ACA kernels, SVD, GEMM batching, memory layout, and threading
belong to numerical-linear-algebra skills.
