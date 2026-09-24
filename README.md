# How to CALMaR

This repository contains a Markdown-first knowledge site for engineers and collaborators working on [CALMaR — Co-designed, Automated Lesion Mapping and Reporting](https://github.com/micmas/calmar).

Its introductory section, **Understanding neuroimaging for CALMaR**, explains the concepts needed to understand, extend, and evaluate the workflow. Changing implementation details and lesion-segmentation benchmark results remain in the CALMaR repository rather than being duplicated here.

The repository's code and original content use the project licence. Reproduced or adapted third-party images retain their own licences and attribution; see [`docs/image-credits.md`](docs/image-credits.md).

## Preview locally

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
mkdocs serve
```

Open `http://127.0.0.1:8000/`.

## Update the guide

- Edit Markdown files under `docs/`.
- Add recurring questions to `docs/faq.md`.
- Add or reorder pages in `mkdocs.yml`.
- Link changing technical results to the relevant CALMaR notebook instead of reproducing them here.

Pushes to `main` validate and publish the site at [how-to-calmar.github.io](https://how-to-calmar.github.io/). GitHub Pages uses the repository's **GitHub Actions** publishing source.

## Relationship to NeurodeskEDU

This guide provides CALMaR-specific concepts and navigation. Executable teaching notebooks should live in or link to [NeurodeskEDU](https://neurodesk.org/edu/intro.html), where they can be tested and launched in a configured environment.
