# 2026-06-24 Review, Revision, and Verification

## Independent Reviewer Comments

1. The recurring metadata-debt critique still applied at the start of this run, but it had shifted. After the June 23 CFD cleanup, the optical/computer-vision category was now the most misleadingly weak part of the catalog because several entries already exposed associated papers upstream while the CSV still made them look like citation-poor prototypes.
2. The flat manual-review queue had become harder to use than the underlying evidence problem. Repeated comments were now less about not knowing *which* entries were weak and more about not knowing whether the remaining debt was primarily paper-link debt, license debt, or unstable archival-link debt.
3. The manuscript and README still overemphasized CFD and utility curation improvements from earlier runs. They needed one more revision cycle to reflect that the catalog also contains a more mature vision-method layer than the generated audit had been showing.
4. The reduced-order category remains the weakest area overall, but it no longer justified spending another full pass there before resolving directly verifiable optical/CV omissions that were suppressing an entire category's apparent maturity.

## Repetition Compared With 2026-06-23

- Repeated from prior day: yes.
- Recurring issue: metadata debt remained the central critique, but the specific bottleneck shifted from CFD infrastructure toward optical/computer-vision entries whose papers had not yet been transferred from upstream READMEs into the catalog.
- Assessment: the June 23 revision was directionally correct but incomplete. It fixed the largest CFD misclassifications, yet it still left the audit overstating uncertainty in the vision layer and gave maintainers too little structure for triaging the remaining queue.

## Substantive Author-Maintainer Revisions

1. Backfilled direct paper links and stronger notes in [`data/resources.csv`](../data/resources.csv) for the current optical/CV and benchmark bottlenecks:
   - `BubbleNet` -> added paper link `https://arxiv.org/abs/2105.07179` from the upstream README and clarified that the repo also points to a Zenodo software record.
   - `BubMask` -> added the Scientific Reports paper `https://www.nature.com/articles/s41598-021-88334-0` from the upstream README.
   - `FluidNexus` -> replaced generic license metadata with verified `MIT`, added the paper link `https://arxiv.org/abs/2503.04720`, and strengthened the notes to describe its linked datasets and future-prediction workflow.
   - `FluidNexus datasets` -> added the same paper link so the benchmark entry is no longer an uncited mirror.
2. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) to compute and render `Remaining Review Focus Counts` so the generated summary and audit now separate paper-link debt, license-review debt, and unstable sharing-link debt.
3. Regenerated [`docs/catalog.md`](../catalog.md), [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and the figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures).
4. Revised [`README.md`](../../README.md) so the repository front page reflects the June 24 optical/CV curation pass and explains the new review-focus breakdown in the audit.
5. Revised [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) and [`paper/arxiv/references.bib`](../../paper/arxiv/references.bib) to document the stronger optical/computer-vision layer and cite BubbleNet, BubMask, and FluidNexus explicitly.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), [`README.md`](../../README.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) for consistency with the new source-verification findings
- Checked for LaTeX toolchain availability: `latexmk` missing, `pdflatex` missing

## Measured Outcome After This Run

- `Partial link coverage` decreased from `21` to `17`.
- `Code + paper/docs` increased from `17` to `19`.
- `Code + data + paper` increased from `15` to `17`.
- `Explicit open license` increased from `25` to `26`.
- `Manual license review` decreased from `12` to `11`.
- `Optical imaging and computer vision` paper-link coverage increased from `50%` to `80%`.
- `Optical imaging and computer vision` license clarity increased from `50%` to `60%`.
- `Simulation and ML benchmarks` paper-link coverage increased from `50%` to `75%`.
- The generated audit now exposes the remaining queue as `15` paper-link issues, `11` license-check issues, and `1` sharing-link issue instead of only a flat resource list.

## Unresolved Risks

1. `Bubble_dynamics_simulation` and `Bubble_dynamics_simulation_CPP` still dominate the reduced-order category because they remain missing both verified licenses and associated paper links.
2. `OpenFOAM` and `MFiX` remain the most important unresolved CFD infrastructure entries for the next pass.
3. `BubbleML`, `BubbleNet`, `BubMask`, and the two Zhou optical repos still need direct upstream license verification even though their paper-link coverage is now improved.
4. Several datasets still need direct paper-link backfill, especially the Harvard Dataverse multimodal pool-boiling dataset, the NASA DASHlink incipient-boiling dataset, the Mendeley `sound of boiling` dataset, and the Dryad physical-descriptor dataset.
5. Manuscript PDF compilation still cannot be verified in this environment because no LaTeX toolchain is installed.
