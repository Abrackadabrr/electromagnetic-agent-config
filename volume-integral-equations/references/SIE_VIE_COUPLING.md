# Coupled surface-volume integral equations

## Block semantics

For surface unknown x_S and volume unknown x_V:

`[ Z_SS  Z_SV ] [x_S] = [b_S]`
`[ Z_VS  Z_VV ] [x_V]   [b_V]`.

Interpretation:

- Z_SS: surface source -> surface observation/testing;
- Z_SV: volume source -> surface observation/testing;
- Z_VS: surface source -> volume observation/testing;
- Z_VV: volume source -> volume observation/testing.

Never obtain a cross block merely by transposing another block unless a proved
reciprocity relation and the discrete pairings justify it.

## Canonical research case: PEC surface + dielectric J-VIE

Assume:

- homogeneous background `epsilon_b,mu_b`;
- PEC surface S with electric surface current `J_S`;
- dielectric region V with polarization current
  `J_V=-i*omega*epsilon_b*chi E`;
- project K/R convention.

The electric field produced by either electric current source uses the same
background map:

`E[J] = i/(omega*epsilon_b) K_b[J]`,

with integration over S or V as appropriate.

### Surface block row

PEC boundary condition:

`(E_inc
 + i/(omega*epsilon_b) K_S[J_S]
 + i/(omega*epsilon_b) K_V[J_V])_tau = 0`.

This defines Z_SS and Z_SV after the selected surface testing/collocation.

### Volume block row

Inside the dielectric:

`J_V - chi K_V[J_V] - chi K_S[J_S]
 = -i*omega*epsilon_b*chi E_inc`.

This follows from the J-VIE definition under the same project convention.

Thus the continuous block semantics are:

- Z_SS: tangential surface trace/test of `i/(omega epsilon_b) K_S`;
- Z_SV: tangential surface trace/test of `i/(omega epsilon_b) K_V`;
- Z_VS: `-chi K_S` tested in V;
- Z_VV: `I-chi K_V`.

Discretization-specific jump terms, self terms, and basis normalizations must be
added according to the actual source/test spaces.

## Contact/junction warning

If the dielectric physically touches the PEC, local singular behavior and
basis compatibility require separate analysis. Independent surface and volume
unknowns do not automatically produce a stable junction discretization.

## Validation

Test each block independently:

1. surface current -> field at volume points;
2. volume current -> tangential field at surface points;
3. volume self operator;
4. coupled solve against a limiting or independently implemented case.
