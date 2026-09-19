# Surface Integral Equation Formulations

## Canonical operator layer

All equations must first be written with project `K`, `R`, and
`G=exp(+ikR)/(4*pi*R)`.

For the thesis current definitions:

`E = i/(omega*epsilon) K[J_e] - R[J_m]`

`H = R[J_e] + i/(omega*mu) K[J_m]`.

Boundary equations are obtained by taking the correct tangential/normal traces
and adding only the jump terms justified by the geometry and trace convention.

## PEC

For a PEC, enforce zero tangential total electric field. Depending on geometry
and conditioning requirements this leads to EFIE or a combined formulation.
MFIE/CFIE jump terms require the closed-surface assumptions appropriate to the
chosen formulation; do not apply a closed-surface `1/2 I` term to an open sheet
without a separate derivation.

## Penetrable dielectric interfaces

Equivalent electric and magnetic surface currents may be introduced and
regional representations combined using continuity of tangential E and H.
PMCHWT/Müller-type equations from external references must be translated from
their original time/normal/current conventions before coding.

## Composite surfaces

Keep region-side contributions explicit until continuity and junction
constraints are unambiguous. Do not assume one geometric edge means one
algebraic current unknown.

## Reference literature

- Rao, Wilton, Glisson (1982), *Electromagnetic scattering by surfaces of
  arbitrary shape*, IEEE TAP 30(3), 409-418, DOI 10.1109/TAP.1982.1142818.
  Classical triangular surface MoM/RWG lineage.
- W. C. Gibson, *The Method of Moments in Electromagnetics*. Use as a source for
  SIE/MoM/junction methodology, but convert from Gibson's harmonic convention
  and operator names.
- J. L. Volakis and K. Sertel, *Integral Equation Methods for
  Electromagnetics*. General SIE/MoM reference.
- The user's thesis is authoritative for the project's `K`, `R`, Green function,
  field representation, and PWC/collocation surface path.
