# Review, Revision, and Verification Note

Date: 2026-06-21

Repeated comments from prior day: yes. The largest recurring critique was that the new audit structure from 2026-06-20 made metadata debt visible but did not yet reduce it enough. Missing paper links and generic license placeholders remained the dominant weakness, especially outside the newest boiling/SciML entries.

## Independent Reviewer Comments

1. The repository still had too much unresolved metadata debt for a catalog that now claims reproducibility-oriented curation. `Partial link coverage` remained the largest evidence bucket, so the previous revision improved visibility more than substance.
2. The audit was still too global. Users could see one overall evidence bar chart, but not which workflow categories had the weakest paper-link coverage or the least clarified license status.
3. Several high-value entries still used generic or unclear license placeholders even though the upstream repositories expose explicit licensing terms. This made the manual-review queue larger than necessary and weakened downstream reuse guidance.
4. The scientific-machine-learning section still under-documented NUCLEUS: the repository had a restrictive source license and an associated 2026 paper, but the catalog and manuscript did not capture that nuance.
5. The manuscript remained unverified at the PDF level, so figure placement and bibliography integration were still a release risk.

## Author-Maintainer Revisions

1. Verified and revised core catalog metadata in [`data/resources.csv`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/data/resources.csv):
   - `BubbleID` license changed from a generic placeholder to `Apache-2.0`
   - `SeqReg` license changed to `Apache-2.0` and linked to the associated Applied Thermal Engineering paper
   - `BURST` license changed to `GPL-3.0`
   - `Aphros` license changed to `MIT`
   - `OpenPIV` license changed to `GPL-3.0`
   - `NUCLEUS` updated from `NOASSERTION` to `CC BY-NC-ND 4.0`, added the new `NUCLEUS-MoE` paper link, and revised notes to reflect its unified multi-fluid scope
2. Extended [`scripts/render_catalog.py`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/scripts/render_catalog.py) to:
   - reject future `source_checked` dates during validation
   - compute category-level metadata coverage
   - generate a new `metadata_coverage_by_category` figure
   - add paper-link, license-clarity, and strong-evidence summary tables to generated docs
3. Regenerated the repository outputs so the new maintenance signals are visible in:
   - [`docs/summary.md`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/docs/summary.md)
   - [`docs/reproducibility_audit.md`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/docs/reproducibility_audit.md)
   - [`figures/metadata_coverage_by_category.png`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/figures/metadata_coverage_by_category.png)
4. Revised [`README.md`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/README.md) to surface the new metadata-coverage dashboard and to frame the audit as a category-targeting maintenance tool rather than only a review queue.
5. Revised the arXiv draft in [`paper/arxiv/main.tex`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/paper/arxiv/main.tex) and [`paper/arxiv/references.bib`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/paper/arxiv/references.bib) to:
   - update the draft date
   - describe the metadata-coverage dashboard in the curation protocol
   - cite the 2026 `NUCLEUS-MoE` paper
   - tighten the argument that category-specific metadata weakness, not just raw catalog growth, should guide future maintenance

## Validation Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Visual inspection of regenerated figures:
  - [`figures/curation_evidence_summary.png`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/figures/curation_evidence_summary.png)
  - [`figures/metadata_coverage_by_category.png`](C:/Users/hanhu/Documents/Programming/Bubble-Dynamics-Research-Tools/figures/metadata_coverage_by_category.png)
- Attempted manuscript compilation:
  - `latexmk -pdf -interaction=nonstopmode main.tex`
  - `pdflatex -interaction=nonstopmode main.tex`
  - Both failed because LaTeX tools are not installed in this environment.

## Current Verification Snapshot

- Evidence bundles: `Code + data + paper = 15`, `Code + paper/docs = 5`, `Partial link coverage = 33`
- License visibility: `Explicit open license = 21`, `Archive/model terms = 15`, `Manual license review = 17`
- Category-level weak spots now clearly identified:
  - reduced-order dynamics: `0%` paper-link coverage, `20%` license clarity
  - general utilities: `0%` paper-link coverage
  - CFD/multiphase: `9%` paper-link coverage

## Unresolved Risks

1. The recurring metadata problem is reduced but not resolved. Reduced-order, utility, and CFD entries still need a focused paper-link and license-verification pass.
2. Some widely used entries such as `BubbleML` still carry generic license wording in the catalog and should be rechecked against upstream repository files in a future run.
3. The manuscript remains uncompiled because no LaTeX toolchain is available here, so PDF-level formatting and bibliography rendering are still unverified.
