# Beam Designer

## Purpose and intended use
Show shear, moment, and deflection diagrams for a beam and provide
preliminary bending and deflection checks. This is an educational and
preliminary-design tool, not a substitute for a complete engineering design
or review.

## Supported scope
- Simply supported and cantilever beams.
- Steel W-shapes from a small curated list, or lumber selected from built-in
  species and grade options.
- Point loads and uniform distributed loads, including partial-span uniform
  loads.
- One entered load case at a time; load combinations are not supported.
- Automatically include beam self-weight.

## Inputs
- Use US customary units: span and load positions in ft, point loads in kip,
  uniform loads in kip/ft, section properties in in-based units, and stress
  in ksi.
- Choose a simply supported beam or a cantilever fixed at the left end.
- Enter a span from 1 to 60 ft. The initial example uses a 20 ft span.
- Choose steel or lumber. Steel uses a curated W-shape list; lumber uses
  nominal 2x8, 2x10, or 2x12 sizes and a built-in species/grade selection.
- Add any number of downward point loads and uniform loads. Each point load
  has a magnitude and position measured from the left end. Each uniform load
  has a magnitude and start/end positions measured from the left end.
- Enter applied loads as service-level loads, excluding self-weight. Add the
  selected beam's self-weight once as a separate downward uniform load, show
  it in the diagram, and include it in all results.
- Use numeric fields with add/remove load rows. Reject negative loads,
  out-of-range positions, zero-length uniform-load intervals, and invalid or
  missing values with a visible message.

## Design basis and assumptions
- Use US customary units. Treat user-entered loads as service-level loads;
  self-weight is added automatically once.
- Use AISC 360 ASD and NDS ASD as references for preliminary bending
  screening only. Clearly identify the simplified allowable stress used and
  do not represent the checks as complete code compliance.
- Check deflection against L/360 for all supported cases.
- Display the material/section properties and assumptions used in each check.
- Use a simplified steel yield-based reference stress and base lumber
  reference values with no design-value adjustments. Mark the built-in
  material values as illustrative and require independent verification
  before any real design use.
- Compute self-weight from the selected section weight for steel and from
  section area and an explicitly stated assumed density for lumber.
- Use downward-positive loads. For cantilevers, the fixed end is at the left.

## Calculations and checks
- Support reactions, shear, and moment from statics.
- Beam deflection.
- Evaluate local shear, moment, and deflection at an interactive probe
  position along the span. At point-load jumps, report shear immediately to
  the right of the probe.
- Bending stress, fb = M/S, compared with the applicable allowable bending
  stress for the selected material and section.
- Deflection compared with L/360.
- Report bending and deflection status separately; do not imply that these
  checks cover all structural limit states.

## Outputs
- A beam diagram showing supports and applied loads.
- Shear, moment, and deflection diagrams.
- A dimensioned cross-section for the selected member. Show overall depth and
  flange width for W-shapes, and actual dressed width and depth for lumber.
  Identify the W-shape profile as schematic where flange/web thicknesses are
  not supplied.
- A live response probe that moves a marker across the beam and diagrams and
  displays local shear, moment, and deflection at that position.
- Separate pass/fail results for bending and deflection, with the values and
  assumptions used for each comparison.

## Look and feel
Clean and professional, with an example beam loaded when the app opens.

## Validation
- 20 ft simply supported W12x26 with a full-span 1 kip/ft uniform load:
  the applied load excludes the beam's 0.026 kip/ft self-weight. With
  self-weight included, maximum support reaction/shear is 10.26 kip,
  maximum moment is 51.3 kip-ft, and maximum deflection is approximately
  0.624 in using Ix = 204 in⁴ and E = 29,000 ksi.
  At the 10 ft probe position, shear is 0 kip, moment is 51.3 kip-ft, and
  deflection is approximately 0.624 in.
- 20 ft simply supported W12x26 with a 1 kip point load at midspan, plus
  self-weight: reactions = 0.760 kip each, maximum moment = 6.30 kip-ft,
  and maximum deflection is approximately 0.065 in.
- 8 ft cantilever W12x26 with a 1 kip point load at the free end, plus
  self-weight: fixed reaction = 1.208 kip, fixed-end moment = 8.832 kip-ft,
  and maximum deflection is approximately 0.054 in.

## Out of scope and limitations
- Continuous beams, buckling/stability, shear capacity, bearing, and
  connections.
- Load combinations and comprehensive code-compliant member design.
- Results must be presented as preliminary; passing the included checks does
  not establish that a beam is safe for construction.

## Details to settle before implementation
- Exact curated W-shape list and official data source/revision for all
  section and lumber properties. The initial built-in values are illustrative,
  not design-table data; the displayed W-shape envelope dimensions also
  require verification against an authoritative source.
- Lumber density and grade reference assumptions, and the standards'
  applicable editions.
- Material adjustments and load combinations are not implemented.
