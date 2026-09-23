# Images used by CALMaR

MRI is a family of measurements. Different acquisitions emphasise different tissue properties, so an algorithm's required modality is part of its scientific specification.

Contributors do not need to diagnose scans or recognise every sequence by sight. They do need to know what information an input contributes and whether a tool was designed for it.

## CALMaR-relevant image types

| Image type | What it helps show | Why the workflow may use it |
|---|---|---|
| T1-weighted MRI | Anatomical structure and tissue boundaries | Chronic-lesion segmentation, brain extraction, registration, atlas mapping |
| T2-weighted or FLAIR MRI | Water-sensitive pathology with strong lesion contrast in many settings | Complementary lesion information and white-matter abnormality context |
| Diffusion-weighted imaging | Restricted water diffusion | Detecting acute ischaemic injury |
| Apparent diffusion coefficient | Quantified diffusion signal | Interpreting whether DWI hyperintensity reflects true restriction |
| Diffusion MRI | Direction-dependent diffusion | Modelling white-matter organisation and structural connectivity |
| Functional MRI | Blood-oxygenation changes related to neural activity | Research on task activity and functional networks |
| CT | Tissue density and blood | Common acute clinical imaging, requiring modality-specific processing |

## Inputs are not interchangeable

Changing the input modality changes the statistical appearance of tissue and pathology. A model trained on chronic T1-weighted scans has not automatically learned acute DWI, FLAIR, or CT.

Before connecting a tool, record:

- Supported modalities and required combinations
- Stroke type and time window represented in development data
- Expected dimensionality, voxel spacing, orientation, and intensity handling
- Whether the tool returns probabilities, labels, or both
- Preprocessing included in the tool versus required upstream

## Multimodal inputs

Multiple images from the same person can offer complementary information, but they must be aligned. A DWI volume, ADC map, FLAIR image, and T1 image may have different grids, distortions, coverage, and spatial resolution.

The workflow must know which image defines the reference space and must preserve every transform used to align the others.

## What image brightness does not mean

MRI intensity is generally not a universal physical scale. Brightness can vary with acquisition settings, reconstruction, scanner, coil, preprocessing, and display window. Code should not assume that the same numeric intensity has the same biological meaning across arbitrary scans unless a method explicitly establishes that relationship.

## Practical rule

Treat the modality, acquisition context, time since stroke, and spatial metadata as part of the input. The voxel array alone is incomplete.
