# Why neuroimaging matters to CALMaR

Post-stroke communication profiles arise from more than the total amount of damaged tissue. Location matters, and damage can interrupt white-matter pathways or alter the function of connected regions that appear structurally intact.

CALMaR therefore treats a lesion mask as the beginning of an analysis, not its clinical conclusion.

## Four levels of information

| Level | Question | Example CALMaR output |
|---|---|---|
| Lesion | Which tissue appears directly damaged? | Lesion mask and volume |
| Region | Which labelled anatomical regions overlap the lesion? | Atlas-overlap table |
| Connection | Which pathways or connected regions may be affected? | Tract involvement or disconnectome |
| Evidence | What has research associated with these features? | Citation-linked knowledge-base findings |

Each level adds context, but also adds assumptions. A direct voxel measurement and an inference based on a normative connectome do not have the same evidential status.

## Biology needed for the workflow

### Tissue and fluid

- **Grey matter** contains neuronal cell bodies and local cortical or subcortical circuitry.
- **White matter** contains long-range axonal pathways connecting regions.
- **Cerebrospinal fluid** occupies ventricles and spaces around the brain. Chronic stroke cavities can resemble CSF on some images, which matters for brain extraction and segmentation.

### Time after stroke

Stroke appearance changes over time. Acute restricted diffusion, subacute oedema, and chronic tissue loss do not present the same segmentation problem. Time since stroke must accompany the image and should influence tool selection, quality-control expectations, and interpretation.

### Distributed language systems

Language depends on interacting cortical, subcortical, white-matter, sensory, motor, and domain-general systems. An atlas label is a useful coordinate system, not a complete explanation of language function.

## Three distinctions to preserve

1. **Damaged tissue versus impaired function.** Structural damage can disrupt function locally and remotely.
2. **Association versus individual prediction.** Group evidence can inform an interpretation without determining an individual outcome.
3. **Biological recovery versus observed outcome.** Therapy access, dosage, comorbidities, environment, goals, and measurement choices also shape the outcome that appears in a dataset.

## Why this matters to engineers

An implementation can be computationally correct and scientifically invalid. Examples include applying an acute-stroke segmenter to unsupported chronic data, silently flipping left and right, using linear interpolation on a label mask, or describing a normative network map as the patient's measured connectivity.

The purpose of this guide is to make those errors visible before they reach a report.
