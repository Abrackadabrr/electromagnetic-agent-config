# Surface junctions

Use this reference only when multiple physical regions/sheets meet or when an
open conductor has two relevant sides.

## Required topology record

For each geometric patch/edge record:

- adjacent physical regions;
- chosen normal(s);
- whether the patch is PEC, dielectric interface, impedance boundary, or port;
- which equivalent currents live on each side;
- current orientation;
- continuity/boundary conditions.

Do not merge region-side unknowns merely because they share a geometric edge.

## PEC/dielectric contacts

If a dielectric is represented by surface equivalent currents, derive the
junction constraints from the chosen regional equivalence principle.

If a dielectric is represented by a volume unknown and the PEC by a surface
current, use the VSIE coupling reference instead of importing pure-SIE
junction elimination rules.

## Open sheets

Do not use a closed-surface MFIE jump identity without checking the trace
theory for the open screen formulation. Keep the two physical sides explicit
when the formulation requires them.
