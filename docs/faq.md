# Recurring questions

## Why can we not resize an MRI like a normal computer-vision image?

The array is tied to physical coordinates through its affine. Naive resizing changes the grid without necessarily preserving anatomy, orientation, or physical voxel size. A model-specific resize may be valid inside a documented pipeline, but it is not a substitute for anatomical registration.

## Why does the affine matter if the image looks correct?

Viewers can display arrays in a plausible orientation while spatial metadata remain wrong or inconsistent. Atlas overlap and transforms use the affine mathematically, so a metadata error can produce an anatomically wrong result without an obvious display failure.

## Why should masks use nearest-neighbour interpolation?

A binary or labelled mask contains categories rather than continuous intensity. Linear interpolation invents intermediate values. If continuous interpolation is deliberately used for a probability map, the workflow must document re-thresholding and its effect.

## What is MNI space?

MNI space is a family of standard brain templates and coordinate systems used to compare participants and use shared atlases. “MNI” alone is incomplete: the exact template, version, resolution, and transform method matter.

## Does CALMaR require a manually traced lesion mask?

No. Automatic lesion segmentation is the scalable primary path. Human review or a manual reference can improve quality, support correction, or enable benchmarking when available. When it is not available, CALMaR should retain the automatic result with its QC status, warnings, mask source, and uncertainty.

## Why review automatic masks?

Algorithms can return plausible outputs for unsupported or corrupted inputs. Review can detect anatomically important failures that summary metrics or automated rules miss. The absence of review should change the qualification attached to the output, not prevent all processing.

## Is a high Dice score enough?

No. Dice is dominated by larger regions and says little about which specific tissue was missed. A small spatial error can alter tract or atlas conclusions. Examine lesion-wise detection, volume bias, boundaries, failure rate, and downstream stability.

## Why can one segmentation tool not handle every scan?

Acute DWI, chronic T1, FLAIR, and CT contain different contrasts and lesion appearances. A tool learns or encodes assumptions about its development data, preprocessing, and target. Those assumptions do not disappear when the software accepts another file.

## Does overlap with a language region prove an impairment?

No. It identifies a spatial relationship under a particular atlas and transform. Functional outcome depends on the broader lesion, connections, individual organisation, time, and many non-imaging factors.

## Is a disconnectome the patient's connectivity?

Not necessarily. Many disconnectomes apply the patient's lesion to connectivity data from a reference population. This is an inferred effect based on normative anatomy, not a direct measurement of the patient's pathways.

## Is lesion-network mapping the patient's fMRI?

No. It usually combines the patient's lesion with a normative functional connectome. The result estimates locations normally connected to the lesion site.

## What is the difference between an analysis and a prediction model?

An atlas overlap can be a deterministic geometric calculation. A knowledge-base lookup can be a rule-based evidence match. A prediction model estimates an outcome from input features learned or specified from data. CALMaR contains several kinds of operation, and reports should name them accurately.

## Where should we document segmentation tools and their performance?

In the [CALMaR benchmark notebook](https://github.com/micmas/calmar/blob/main/lesion-segmentation-benchmark.ipynb). This guide should link to that output rather than maintain a second tool registry that will quickly become stale.

## What should become a new page?

A recurring question deserves a page when its answer affects multiple CALMaR stages or requires diagrams, examples, or references. Short answers can remain here. Use the repository's recurring-question issue template to capture new candidates.
