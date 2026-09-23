# Contributing

The site is designed to grow from real questions asked during CALMaR development.

## Small edits

Use the edit icon on any page, change the Markdown file, and open a pull request.

## Add a recurring question

1. Open an issue using the **Recurring question** template.
2. Record the question in the language originally used.
3. Identify the affected workflow stage or analysis.
4. Add a concise answer to `docs/faq.md`, or create a new page if the answer needs diagrams, examples, or several references.
5. Link to the relevant CALMaR code or NeurodeskEDU activity.

## Keep content in the right place

| Content | Home |
|---|---|
| Stable neuroimaging concept | This guide |
| Current CALMaR operation | CALMaR repository or notebook |
| Segmentation comparison and benchmark result | Benchmark notebook |
| Detailed QC rating definitions | CALMaR QC rubric |
| Executable teaching notebook | NeurodeskEDU |
| Evidence about aphasia, impairment, or therapy | CALMaR knowledge base |

## Page pattern

Most pages should answer:

1. Why does CALMaR need this?
2. What goes in and what comes out?
3. What is measured directly and what is inferred?
4. What can fail?
5. How should the result be checked?
6. Where are the current implementation and practical exercise?

## Writing principles

- Write for engineers who may be new to neuroimaging.
- Define domain terms when they first appear.
- Connect concepts to a CALMaR stage or output.
- Distinguish direct measurement, derived result, normative inference, literature association, and clinical interpretation.
- Prefer a specific limitation over a generic disclaimer.
- Avoid copying version numbers, rankings, or thresholds that belong in executable project outputs.

## Validate locally

```bash
mkdocs build --strict
```

The GitHub Pages workflow runs the same strict build for every push to `main`.
