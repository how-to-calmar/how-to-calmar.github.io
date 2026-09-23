# Meta-analytic decoding

Meta-analytic decoding relates a brain map to terms or topics extracted from a large neuroimaging literature. CALMaR can use this as an exploratory bridge between spatial results and published functional associations.

## Forward and reverse questions

- **Forward inference:** where does the literature report activity for a selected task or term?
- **Reverse decoding:** which terms are statistically associated with a supplied brain map?

These are not interchangeable. Reverse decoding is especially vulnerable to overinterpretation when base rates, study selection, and correlated terms are ignored.

## What the output represents

A decoding score summarises an association between the supplied map and a literature-derived term map under a particular method and database version.

It does not establish that the patient:

- Performed the task represented by the term
- Has an impairment named by the term
- Uses the same functional organisation as the aggregated studies
- Should receive a therapy associated with that term

## CALMaR wording

Prefer language such as:

> The affected map overlaps literature-derived spatial associations for these terms.

Avoid language such as:

> The scan predicts that the patient has these deficits.

## Implementation information to retain

- Source database and version
- Included study domain
- Decoding algorithm
- Input map and space
- Thresholding and masking
- Score definition
- Multiple-comparison or ranking approach
- Whether the output is exploratory

## NiMARE

[NiMARE](https://nimare.readthedocs.io/) provides tools for neuroimaging meta-analysis and decoding. CALMaR contributors should understand the selected decoder and its assumptions rather than treating a returned term list as self-validating.
