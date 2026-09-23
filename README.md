# Understanding neuroimaging for CALMaR

This repository contains a Markdown-first knowledge site for engineers and collaborators working on [CALMaR](https://github.com/micmas/calmar).

The guide explains the neuroimaging concepts needed to understand, extend, and evaluate CALMaR. Changing implementation details and lesion-segmentation benchmark results remain in the CALMaR repository rather than being duplicated here.

## Preview locally

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
mkdocs serve
```

Open `http://127.0.0.1:8000`.

## Update the guide

- Edit Markdown files under `docs/`.
- Add recurring questions to `docs/faq.md`.
- Add or reorder pages in `mkdocs.yml`.
- Link changing technical results to the relevant CALMaR notebook instead of reproducing them here.

Pushes to `main` build and publish the site through GitHub Pages. In the GitHub repository settings, set **Pages > Build and deployment > Source** to **GitHub Actions**.

## Relationship to NeurodeskEDU

This guide provides CALMaR-specific concepts and navigation. Executable teaching notebooks should live in or link to [NeurodeskEDU](https://neurodesk.org/edu/intro.html), where they can be tested and launched in a configured environment.
