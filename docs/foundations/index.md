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

<figure class="calmar-figure">
<div class="tissue-comparison">
  <div class="tissue-panel">
    <div class="tissue-panel__title">T1-weighted</div>
    <div class="tissue-panel__image">
      <img src="../assets/open-imaging/normal-t1-axial.jpg" alt="Axial T1-weighted MRI with tissue callouts">
      <svg viewBox="0 0 100 100" preserveAspectRatio="none" aria-hidden="true">
        <defs><marker id="t1-arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="4" markerHeight="4" orient="auto"><path d="M0 0L10 5L0 10Z" fill="#55d3ca"/></marker></defs>
        <line x1="20" y1="14" x2="50" y2="43" marker-end="url(#t1-arrow)"/>
        <line x1="20" y1="88" x2="26" y2="54" marker-end="url(#t1-arrow)"/>
        <line x1="80" y1="88" x2="47" y2="62" marker-end="url(#t1-arrow)"/>
      </svg>
      <span class="tissue-callout tissue-callout--csf">CSF · dark</span>
      <span class="tissue-callout tissue-callout--gm">Grey matter</span>
      <span class="tissue-callout tissue-callout--wm">White matter</span>
    </div>
  </div>
  <div class="tissue-panel">
    <div class="tissue-panel__title">T2-weighted</div>
    <div class="tissue-panel__image">
      <img src="../assets/open-imaging/normal-t2-axial.jpg" alt="Axial T2-weighted MRI with tissue callouts">
      <svg viewBox="0 0 100 100" preserveAspectRatio="none" aria-hidden="true">
        <defs><marker id="t2-arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="4" markerHeight="4" orient="auto"><path d="M0 0L10 5L0 10Z" fill="#55d3ca"/></marker></defs>
        <line x1="20" y1="14" x2="50" y2="43" marker-end="url(#t2-arrow)"/>
        <line x1="20" y1="88" x2="26" y2="54" marker-end="url(#t2-arrow)"/>
        <line x1="80" y1="88" x2="47" y2="62" marker-end="url(#t2-arrow)"/>
      </svg>
      <span class="tissue-callout tissue-callout--csf">CSF · bright</span>
      <span class="tissue-callout tissue-callout--gm">Grey matter</span>
      <span class="tissue-callout tissue-callout--wm">White matter</span>
    </div>
  </div>
</div>
<figcaption><strong>Figure 1. Tissue contrast on T1- and T2-weighted MRI.</strong> These are real images from a matched normal-brain series. CSF is dark on T1 and bright on T2; white and grey matter also reverse their relative contrast. Images by <a href="https://commons.wikimedia.org/wiki/User:511KeV">511KeV</a>, with CALMaR labels added, licensed <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a>. See <a href="../image-credits/">image credits</a>.</figcaption>
</figure>

### Time after stroke

Stroke appearance changes over time. Acute restricted diffusion, subacute oedema, and chronic tissue loss do not present the same segmentation problem. Time since stroke must accompany the image and should influence tool selection, quality-control expectations, and interpretation.

<figure class="calmar-figure" markdown>
![Acute and subacute stroke examples across diffusion, vascular, perfusion, T1-weighted and T2-weighted imaging.](../assets/open-imaging/macintosh-graham-2013-figure-2.webp)
<figcaption><strong>Figure 2. Acute and subacute stroke across several MRI-derived images.</strong> The upper row shows an acute case using DWI, time-of-flight angiography, cerebral blood-flow and arterial-transit-time images. The lower row shows a second lesion on T1- and T2-weighted MRI. Reproduced from Figure 2 of <a href="https://doi.org/10.3389/fneur.2013.00060">MacIntosh and Graham (2013)</a>, licensed <a href="https://creativecommons.org/licenses/by/3.0/">CC BY 3.0</a>.</figcaption>
</figure>

<figure class="calmar-figure calmar-figure--narrow" markdown>
![Chronic and subacute stroke lesions on FLAIR MRI acquired at 3 Tesla and 7 Tesla.](../assets/open-imaging/madai-2012-figure-1.jpg)
<figcaption><strong>Figure 3. Chronic stroke on FLAIR.</strong> White arrowheads identify chronic lesions; red arrowheads identify a subacute lesion; asterisks mark tissue-defect areas. The 3 T versus 7 T comparison is secondary here—the important point is that chronic injury has a different structural appearance from acute diffusion restriction. Reproduced from Figure 1 of <a href="https://doi.org/10.1371/journal.pone.0037631">Madai et al. (2012)</a> under the article's <a href="https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0037631">Creative Commons Attribution licence</a>.</figcaption>
</figure>

### Distributed language systems

Language depends on interacting cortical, subcortical, white-matter, sensory, motor, and domain-general systems. An atlas label is a useful coordinate system, not a complete explanation of language function.

<figure class="calmar-figure" markdown>
![Original schematic of a left-lateralized core language network interacting through dorsal and ventral pathways with perceptual, motor and broader cognitive systems.](../assets/distributed-language-systems.svg)
<figcaption><strong>Figure 4. Distributed systems supporting language.</strong> This is an original conceptual synthesis, not a reproduction of either paper's figure. It combines the dorsal–ventral account of <a href="https://doi.org/10.1038/nrn2113">Hickok and Poeppel (2007)</a> with the distinction between the core language-selective network and interacting perceptual, motor and broader cognitive systems discussed by <a href="https://doi.org/10.1038/s41583-024-00802-4">Fedorenko, Ivanova and Regev (2024)</a>.</figcaption>
</figure>

## Three distinctions to preserve

1. **Damaged tissue versus impaired function.** Structural damage can disrupt function locally and remotely.
2. **Association versus individual prediction.** Group evidence can inform an interpretation without determining an individual outcome.
3. **Biological recovery versus observed outcome.** Therapy access, dosage, comorbidities, environment, goals, and measurement choices also shape the outcome that appears in a dataset.

## Why this matters to engineers

An implementation can be computationally correct and scientifically invalid. Examples include applying an acute-stroke segmenter to unsupported chronic data, silently flipping left and right, using linear interpolation on a label mask, or describing a normative network map as the patient's measured connectivity.

The purpose of this guide is to make those errors visible before they reach a report.
