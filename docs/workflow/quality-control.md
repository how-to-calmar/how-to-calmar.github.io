# Quality control

Quality control asks whether an output is fit for its next use. A file can exist, load successfully, and still be unsuitable for analysis.

## Layers of QC

| Layer | Example checks |
|---|---|
| Input | Modality, dimensions, affine, orientation, coverage, corruption |
| Brain extraction | Brain tissue retained, skull excluded, lesion not removed |
| Segmentation | Coverage, false positives, laterality, topology, boundary quality |
| Registration | Anatomical alignment, left-right integrity, lesion placement after warp |
| Analysis | Plausible region labels, tract results, and map coverage |
| Reporting | Mask source, QC status, uncertainty, and provenance visible |

## Automated and human QC

Automated checks should run for every case. Human review can add valuable anatomical judgement when available, but the system should not depend on a manually traced mask to complete.

Automated checks can detect:

- Empty or nearly whole-brain masks
- Implausible lesion volume
- Extracranial voxels
- Unexpected hemisphere
- Fragmentation or excessive component count
- Mismatch between image and mask geometry
- Missing transforms or sidecars
- Atlas-grid coverage errors

They cannot guarantee that a mask follows the true lesion boundary or distinguish every lesion from every mimic.

## QC status should travel downstream

A compact machine-readable record might include:

```json
{
  "mask_source": "automatic",
  "automated_qc": "pass_with_warnings",
  "human_review": "not_available",
  "warnings": ["small_disconnected_cluster"],
  "suitable_for": ["exploratory_atlas_overlap"],
  "not_validated_for": ["individual_clinical_prediction"]
}
```

The exact schema can change, but the distinction between automatic result, human-reviewed result, and expert reference should remain explicit.

## Error propagation

QC should occur before expensive or interpretive stages. If brain extraction is poor, fixing it after atlas overlap does not rescue the derived results. Where the workflow continues after a warning, later outputs must inherit that warning.

## CALMaR reference

The current stage-specific language and repair guidance live in the [CALMaR QC rubric](https://github.com/micmas/calmar/blob/main/QC_RUBRIC.md). Keep detailed operational ratings there so the notebook and rubric can evolve together.

## Review questions

- Which image and space am I looking at?
- Which mask source is displayed?
- Has the lesion been removed by brain extraction?
- Are unexpected clusters anatomically plausible?
- Does native-space placement agree with transformed placement?
- Would the observed error change the planned downstream analysis?
