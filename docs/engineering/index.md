# Working on CALMaR

CALMaR development is workflow engineering with scientific contracts. A change is complete when it runs reproducibly and preserves the meaning of the data.

## Map the code change to the scientific consequence

| If you change | Check |
|---|---|
| Input discovery | Correct subject, session, modality, and metadata selection |
| Orientation handling | Left-right integrity and affine preservation |
| Brain extraction | Cortex, cerebellum, brainstem, and lesion retained |
| Segmentation threshold | Small-lesion sensitivity, false positives, volume bias |
| Post-processing | Topology, multifocal lesions, provenance of each operation |
| Registration | Native and template alignment, transformation direction |
| Interpolation | Continuous values versus discrete masks and labels |
| Atlas | Version, space, resolution, label table, background handling |
| Disconnectome | Reference population, threshold, space, interpretation wording |
| Decoder | Database version, term definitions, score meaning |
| Report | Mask source, QC status, evidence layer, uncertainty, citation |

## Pipeline contracts

For every stage, document:

```yaml
stage: example-stage
inputs:
  modality: T1w
  space: native
outputs:
  type: binary_mask
  space: native
method:
  tool: example
  version: 1.2.3
  parameters: {}
quality_control:
  automated: required
  human_review: optional
provenance:
  record_transform: true
  record_runtime: true
```

This is a conceptual example, not a CALMaR schema requirement.

## Definition of done

- Intended input population and modalities are stated.
- Spatial assumptions are explicit and checked.
- Outputs carry space, method, version, and parameters.
- Failures and warnings are machine-readable.
- Re-running does not silently overwrite reviewed results.
- Representative normal and failure cases are tested.
- Downstream scientific outputs are compared, not only intermediate arrays.
- Documentation explains the result without overclaiming.
- Patient-derived data do not enter logs, external services, or fixtures.

## Where changing details belong

- Workflow code and operational instructions: [CALMaR repository](https://github.com/micmas/calmar)
- Segmentation tools and benchmark results: [benchmark notebook](https://github.com/micmas/calmar/blob/main/lesion-segmentation-benchmark.ipynb)
- Stage-specific QC definitions: [QC rubric](https://github.com/micmas/calmar/blob/main/QC_RUBRIC.md)
- General executable teaching: [NeurodeskEDU](https://github.com/neurodesk/neurodeskedu)
- Stable CALMaR concepts and recurring explanations: this guide

## Useful review pattern

When reviewing a pull request, ask two sets of questions:

**Software:** Does it run, fail clearly, preserve provenance, and remain maintainable?

**Scientific:** Does the input match the method, is spatial meaning preserved, and can the output support the wording shown to users?
