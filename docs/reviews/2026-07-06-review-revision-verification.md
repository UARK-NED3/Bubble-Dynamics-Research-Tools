# 2026-07-06 Review, Revision, and Verification

## Independent Reviewer Comments

1. The July 5 dataset ladder improved data-selection trust, but a similar usability gap still remained one level up: users could now rank datasets, yet they still had to mentally combine quick picks, audit tables, and category knowledge to decide what tool to try first for a full workflow.
2. That recurrence mattered because the repository had already accumulated good curation signals, but those signals were still scattered across multiple pages. A scientifically strong catalog can still be practically weak if first-use decisions remain implicit.
3. The current quickstart and README also compressed unlike cases into the same recommendation style. A pool-boiling segmentation stack, a compressible shock-bubble CFD solver, and a reuse-restricted surrogate-model package should not all look equally ready without an explicit trust signal and caveat next to them.
4. A second, smaller curation issue persisted in row-level source notes. The BubbleML and Zhou repository entries had enough public upstream detail to support more specific notes than the prior generic descriptions, and keeping those rows vague would weaken both the new task guidance and the blocker model that depends on note text.

## Repetition Compared With 2026-07-05

- Repeated from prior day: yes, at the pattern level.
- Recurring issues:
  - the repository still needed a stronger `start here first` layer rather than expecting users to infer first actions from several separate summaries;
  - the July 5 dataset ladder fixed that problem for data rows, but not yet for end-to-end workflows that combine code, data, and solver choices;
  - source-note specificity still mattered because the new user-guidance layer depends on accurate row-level evidence statements.
- Assessment: the July 5 pass was useful but only partially sufficient. It solved trust ordering for datasets, yet the same decision-readiness critique remained at the workflow layer, which justified another renderer-level revision instead of a prose-only cleanup.

## Substantive Author-Maintainer Revisions

1. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) with a generated `Workflow Starter Matrix` that maps common bubble-dynamics workflows to:
   - a recommended first-stop tool;
   - supporting dataset or benchmark rows;
   - a compact trust signal;
   - a `why this first` explanation;
   - the main caveat that should still limit blind reuse.
2. Regenerated [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) so the new starter matrix appears alongside the existing dataset ladder and reduced-order triage tables rather than forcing users to synthesize guidance across multiple pages.
3. Refreshed source-verified catalog rows in [`data/resources.csv`](../../data/resources.csv) for:
   - `BubbleML`, whose public GitHub page still exposes paper, dataset-docs, examples, and reproducibility-capsule evidence but still does not surface a standalone LICENSE file;
   - `Bubble detection and tracking AI-based YOLO tracking algorithm`, whose public README now explicitly records about 90% condensing-bubble detection plus extracted thermal-hydraulic metrics;
   - `Robust TH analysis method for bubbles using AI`, whose public README now explicitly records about 95% condensing-bubble detection plus void-fraction, interfacial-area, Nusselt-number, and nucleation-site outputs.
4. Revised [`README.md`](../../README.md), [`docs/quickstart.md`](../quickstart.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the human-facing narrative now explains the July 6 workflow-matrix revision and points readers to the generated decision aid instead of leaving it as an audit-only feature.
5. Regenerated [`docs/catalog.md`](../catalog.md) and [`docs/discovery_candidates.md`](../discovery_candidates.md) during validation so the updated source notes and rendered guidance stay synchronized across the repo.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- `python scripts/discover_candidates.py --output docs/discovery_candidates.md`
- Checked regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), [`docs/catalog.md`](../catalog.md), [`docs/quickstart.md`](../quickstart.md), [`README.md`](../../README.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) for:
  - the new `Workflow Starter Matrix` sections;
  - BubbleML and the Zhou repositories propagating refreshed source notes;
  - consistent July 6 narrative updates across the README, quickstart, and manuscript;
  - unchanged dataset-ladder and reduced-order-triage logic alongside the new workflow guidance.
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment.

## Measured Outcome After This Run

- The repository now exposes three distinct decision layers instead of two: dataset trust ordering, reduced-order trust ordering, and workflow-level first-stop guidance.
- New users no longer need to merge quick picks, audit tables, and category summaries by hand just to decide which tool to try first for a common research task.
- BubbleML and the Zhou repository rows now carry more specific public-source evidence, which improves both user interpretation and future blocker classification stability.

## Unresolved Risks

1. The workflow starter matrix is intentionally curated and opinionated; if future rows materially change the best first-stop choice for a workflow, maintainers must keep the mapping current.
2. BubbleML still carries manual license-review debt because the public GitHub repository page still did not surface a standalone LICENSE file during direct verification.
3. The Zhou repositories still do not surface explicit license files or repository-level license badges, so redistribution and derivative-work rights remain unclear even though their technical notes are now stronger.
4. Several core datasets still have unresolved public paper discoverability or absent paper evidence, especially the NASA DASHlink incipient-boiling row, the Harvard Dataverse multimodal row, and the Mendeley `sound of boiling` row.
5. Manuscript PDF compilation still cannot be validated in this environment because no LaTeX toolchain is installed.
