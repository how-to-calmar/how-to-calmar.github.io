# Types of analysis

CALMaR analyses answer different questions about the same lesion. Their outputs should not be collapsed into one undifferentiated notion of “brain damage.”

| Analysis | Main question | Key dependency |
|---|---|---|
| Lesion description | How large is the mask and where is it? | Segmentation quality |
| Atlas overlap | Which labelled regions directly overlap it? | Registration, atlas choice |
| Tract overlap | Which reference pathways intersect it? | Tract definition and space |
| Disconnectome | Which structural connections may be disrupted? | Normative or measured connectivity model |
| Lesion-network mapping | Which functionally connected regions may be affected remotely? | Normative functional-connectivity data |
| Meta-analytic decoding | Which research terms are associated with the affected map? | Literature database and decoding method |
| Lesion-symptom analysis | Which lesion features are statistically associated with behaviour? | Cohort, outcome, covariates, model |
| Knowledge-base matching | What published findings relate to measured features? | Evidence schema and review quality |

## Direct measurements and derived inferences

A useful reporting hierarchy is:

1. **Observed or segmented:** the image and lesion mask.
2. **Spatially derived:** overlap calculated after documented transforms.
3. **Normatively inferred:** disconnection or connectivity estimated from another cohort.
4. **Literature associated:** functions or outcomes linked through published group findings.
5. **Clinically interpreted:** meaning considered alongside assessment, history, goals, and trajectory.

Each step can be useful. Each step must preserve its provenance and uncertainty.

## Analyses not models

Many CALMaR operations are deterministic calculations or evidence lookups rather than newly trained prediction models. Atlas overlap, for example, calculates a geometric intersection. The fact that a later report interprets that intersection does not turn the overlap computation into a learned model.
