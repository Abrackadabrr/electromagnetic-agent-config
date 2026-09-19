# Surface Junctions

Composite conducting/dielectric SIE problems can have more than two material
sides meeting at an edge. Treat region-side unknowns, geometry orientation, and
physical continuity as separate layers.

For Gibson-derived junction rules:

- use Gibson only as a topology/current-constraint source;
- translate all field/operator signs into project convention;
- preserve explicit orientation signs rather than hiding them in indexing;
- distinguish opposite sides of an open conductor from opposite material sides
  of a dielectric interface;
- do not place magnetic equivalent currents inside a PEC region.

If a problem is instead formulated as VSIE with volume currents in the
dielectric and surface currents only on PEC, load `volume-integral-equations` and
use the VSIE coupling rules there. Do not force a PMCHWT surface treatment onto a
volume-modeled dielectric merely because a dielectric/PEC junction exists.
