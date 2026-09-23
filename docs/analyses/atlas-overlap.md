# Atlas overlap

An atlas assigns labels to locations in a reference brain. Atlas overlap calculates how much of a lesion mask intersects each label.

## What is calculated

For a region \(R\) and lesion \(L\), common summaries include:

- Number of lesion voxels inside the region
- Proportion of the lesion falling inside the region
- Proportion of the region affected by the lesion
- Lesion volume within the region

These denominators answer different questions. Reports should name them explicitly.

## Required conditions

- Lesion and atlas must occupy compatible physical spaces.
- Label masks should remain discrete during resampling.
- The atlas resolution and coverage must be known.
- Atlas labels and version must be recorded.
- Registration quality must be sufficient for the scale of the regions being reported.

## What atlas overlap can say

Atlas overlap can state that a defined portion of the lesion occupies a labelled region under a specified atlas and transform.

It cannot, on its own, prove that:

- The patient has the function associated with that region impaired
- Every voxel in the region has the same role
- A named syndrome is present
- A particular therapy will work
- An atlas derived from a group precisely represents this individual's anatomy

## Atlas choice matters

Atlases divide the brain according to different anatomical, connectivity, functional, or histological principles. Coarse regions can be robust but nonspecific. Fine parcellations can appear precise while becoming more sensitive to registration error.

CALMaR should report the atlas, version, space, resolution, and measure used rather than presenting region names as self-evident facts.

## Engineering checks

- Confirm no silent resampling to a mismatched grid.
- Test masks at region boundaries.
- Test lesions outside atlas coverage.
- Verify label lookup tables and background values.
- Pin expected overlaps for small regression fixtures.
- Keep voxel counts separate from physical volumes.
