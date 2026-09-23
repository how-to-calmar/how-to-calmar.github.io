# Tracts and disconnection

A lesion can affect communication by damaging cortex, interrupting white-matter pathways, or disturbing connected networks. Disconnection analyses estimate effects that lesion volume and regional overlap may miss.

## Tract overlap

Tract overlap intersects the lesion with a reference tract representation. The tract may be binary, probabilistic, thresholded, or derived from a population atlas.

The output depends on:

- Which tract definition is used
- Whether the tract is population-derived or individually measured
- The probability threshold
- Registration accuracy
- Whether overlap represents any contact or a quantified burden

## Structural disconnectome

A structural disconnectome estimates pathways likely to pass through or be interrupted by the lesion. It often uses tractography from healthy reference participants rather than diffusion data acquired from the patient.

This can provide a useful hypothesis about affected connections. It should be described as normative or inferred when that is what it is.

## Direct diffusion MRI

Patient diffusion MRI can measure diffusion properties in that individual's brain, but interpretation after stroke remains affected by crossing fibres, tissue damage, oedema, acquisition quality, modelling choices, and tractography limitations.

Streamlines are model outputs. They are not direct images of axons.

## Lesion-network mapping

Lesion-network mapping uses a reference functional-connectivity dataset to identify regions normally connected to the lesion location. It can estimate remote network effects without acquiring patient fMRI.

It does not measure the patient's own functional connectivity. Reports should distinguish:

- Patient-derived lesion location
- Reference connectome source
- Mapping and threshold method
- Direct overlap versus remote network result

## Questions for implementation

- Is this individual measurement or normative inference?
- Which population generated the reference data?
- Which space and resolution are required?
- How are negative and positive connectivity handled?
- Which threshold determines that a tract or region is affected?
- How will uncertainty in the lesion mask alter the result?
