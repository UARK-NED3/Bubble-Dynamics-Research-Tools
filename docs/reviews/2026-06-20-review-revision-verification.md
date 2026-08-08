# Review, Revision, and Verification Note

Date: 2026-06-20

Repeated comments from prior day: none; first run.

## Independent Reviewer Comments

1. Scientific scope was skewed toward boiling vision and surrogate modeling, with weak representation of compressible bubble, cavitation, and shock-bubble simulation workflows.
2. The catalog counted resources by category but did not expose curation quality well enough. Users could not quickly distinguish strong evidence bundles from partial-link entries or generic license placeholders.
3. The manuscript overinterpreted the catalog as a field trend story without enough caution that it is a curated maintenance artifact rather than a systematic literature census.
4. The timeline figure was difficult to read because the legend and stacked bars emphasized category labels more than yearly totals.
5. Repository usability was limited by the absence of a dated review log and by the lack of a generated page focused on reproducibility and manual-review priorities.

## Author-Maintainer Revisions

1. Added MFC as a new CFD catalog entry after source verification against the official GitHub repository and cited 2026 Computer Physics Communications paper. This expands coverage toward compressible multiphase, cavitation, and shock-bubble regimes.
2. Extended [`scripts/render_catalog.py`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/scripts/render_catalog.py) to:
   - validate ISO dates in `source_checked`
   - generate [`docs/reproducibility_audit.md`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/docs/reproducibility_audit.md)
   - compute evidence tiers and license-visibility buckets
   - produce a new `curation_evidence_summary` figure
   - improve timeline readability with short legend labels and yearly total annotations
3. Revised [`README.md`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/README.md), [`docs/quickstart.md`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/docs/quickstart.md), and [`docs/curation_workflow.md`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/docs/curation_workflow.md) so users are directed to evidence and license checks before reuse.
4. Revised the arXiv draft in [`paper/arxiv/main.tex`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/paper/arxiv/main.tex) and [`paper/arxiv/references.bib`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/paper/arxiv/references.bib) to:
   - update the catalog size to 54 entries
   - discuss the new reproducibility audit
   - add MFC to the scientific scope and workflow recommendations
   - temper trend claims with stronger evidence-oriented framing

## Validation Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Visual inspection of regenerated figures:
  - [`figures/resource_timeline.png`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/figures/resource_timeline.png)
  - [`figures/curation_evidence_summary.png`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/figures/curation_evidence_summary.png)

## Unresolved Risks

1. The audit now makes the largest remaining weakness explicit: many entries still rely on partial link coverage or generic license labels such as `Repository license`.
2. Several datasets and code repositories still lack associated paper links in `data/resources.csv`; future runs should prioritize filling those gaps for the highest-impact entries.
3. I did not build the LaTeX manuscript to PDF in this run, so the new figure placement and bibliography integration were not typeset-verified.
