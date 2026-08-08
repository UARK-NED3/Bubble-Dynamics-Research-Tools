# 2026-06-25 Review, Revision, and Verification

## Independent Reviewer Comments

1. The same core critique from earlier runs still held at the start of this pass: metadata debt remained the main limitation, but it was now concentrated enough that the repository needed direct row-level verification and a sharper audit view rather than another generic discussion of “missing metadata.”
2. The optical/computer-vision layer was still being understated by the generated audit because BubbleNet and BubMask already exposed explicit upstream licenses while the CSV continued to classify them as generic repository-license cases.
3. The audit had improved over the last few days, but repeated comments were still likely because the queue was only separated by issue type, not by issue type within category. That made it hard to see that datasets now dominate paper-link debt while reduced-order dynamics remains the weakest mixed paper-plus-license category.
4. CFD infrastructure remained partly under-curated. OpenFOAM and MFiX had strong official project pages and established citation anchors, but the catalog still needed a clearer distinction between what was directly verified and what remains unresolved about their canonical software-paper and license metadata.

## Repetition Compared With 2026-06-24

- Repeated from prior day: yes.
- Recurring issue: metadata debt remained the central critique. Compared with June 24, the recurrence was more specific: the previous revision improved queue visibility, but it still did not verify obvious upstream licenses for key vision entries or show category-level concentration of the remaining debt.
- Assessment: the June 24 revision was useful but insufficient. It clarified *what type* of debt remained, but not strongly enough *where* that debt was structurally concentrated or which rows were still false negatives after direct source checking.

## Substantive Author-Maintainer Revisions

1. Revised [`data/resources.csv`](../data/resources.csv) after direct source verification:
   - `BubbleNet` -> replaced `Repository license` with verified `MIT` and strengthened notes to reflect the upstream MIT license plus linked Zenodo software record.
   - `BubMask` -> replaced `Repository license` with verified `MIT` and strengthened notes to reflect the shipped MIT license file and linked Scientific Reports paper.
   - `OpenFOAM` -> backfilled the catalog `paper_url` with the official project/citation anchor already used by the manuscript’s Jasak et al. software citation and clarified the notes accordingly.
   - `MFiX` -> strengthened notes to reflect direct verification of the NETL product page, theory guides, and citations database, while preserving manual-review status because no concrete SPDX-style license or single canonical software-paper URL was exposed on the public page.
   - `Unveiling hysteresis...` and `Generalizable physical descriptors...` datasets -> strengthened notes after direct Dryad-page inspection to capture what was verifiably exposed upstream and why they still remain in the paper-link queue.
2. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) to compute and render `Review Debt By Category`, including a new figure `review_debt_by_category.*` and matching tables in the generated summary and reproducibility audit.
3. Regenerated [`docs/catalog.md`](../catalog.md), [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and the mirrored figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures).
4. Revised [`README.md`](../../README.md) so the front page now reflects the June 25 maintenance focus: verified MIT licensing in the optical/CV layer and a category-by-category view of the remaining review debt.
5. Revised [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) to update the draft date, document the June 25 audit changes, explain the corrected optical/CV license picture, and add the new review-debt figure plus interpretation.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- `python scripts/render_catalog.py --validate-only` (post-edit recheck)
- Checked regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), [`README.md`](../../README.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) for consistency with the new source-verification findings
- Confirmed the new figure outputs exist in both repo and manuscript figure directories
- Checked for LaTeX toolchain availability in prior runs; `latexmk` and `pdflatex` remain unavailable in this environment, so manuscript PDF compilation still could not be verified here

## Measured Outcome After This Run

- `Partial link coverage` decreased from `17` to `16`.
- `Code + paper/docs` increased from `19` to `20`.
- `Explicit open license` increased from `26` to `28`.
- `Manual license review` decreased from `11` to `9`.
- `Optical imaging and computer vision` license clarity increased from `60%` to `80%`.
- `CFD and multiphase simulation` paper-link coverage increased from `64%` to `73%`.
- The remaining queue is now exposed both by issue type and by category:
  - `14` `no paper link`
  - `9` `license check`
  - `1` `sharing link`
  - with the heaviest concentration in `Datasets` (`8` issues) and `Reduced-order bubble dynamics` (`6` issues)

## Unresolved Risks

1. `Bubble_dynamics_simulation` and `Bubble_dynamics_simulation_CPP` still dominate the reduced-order category because they remain missing both verified licenses and associated paper links.
2. `MFiX`, `OpenFOAM interFoam guide`, and `OpenFOAM dispersed multiphase guide` remain the key CFD infrastructure entries with unresolved license-review ambiguity or incomplete canonical citation handling.
3. Several dataset rows still lack stable paper URLs even after direct archive-page inspection, especially the Harvard Dataverse multimodal pool-boiling dataset, the NASA DASHlink incipient-boiling dataset, the Mendeley `sound of boiling` dataset, and the Dryad physical-descriptor dataset.
4. `BubbleML`, `BURST`, `Boiling Learning`, and the two Zhou optical repos remain the most important non-dataset rows still limiting full paper-link or license clarity outside the reduced-order category.
5. Manuscript PDF compilation still cannot be verified in this environment because no LaTeX toolchain is installed.
