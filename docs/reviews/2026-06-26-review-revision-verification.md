# 2026-06-26 Review, Revision, and Verification

## Independent Reviewer Comments

1. The core critique still repeated from prior runs: metadata debt remains the main scientific and usability limitation, but it is no longer a field-wide problem. It is concentrated in a narrow set of dataset paper-link rows and a stubborn reduced-order bubble-dynamics cluster whose missing licenses and citations have now recurred for nearly a week.
2. The June 25 audit improvement was useful, but still insufficient on its own because issue-type and category summaries do not force action on the hardest rows. A ranked row-level frontier was needed so repeated comments stop diffusing into a generic backlog.
3. Several rows had become weaker than they looked because their notes no longer reflected the latest direct source evidence. In particular, the Mendeley `sound of boiling` dataset still carried generic archive terms even though the archive exposes a concrete `CC BY 4.0` license, and the NASA DASHlink row needed refreshed notes after the 2025 page update.
4. The reduced-order category remains the weakest part of the repository not because it has been ignored, but because direct rechecking still does not surface stronger upstream evidence. That distinction matters for manuscript honesty: the repo should now say more clearly when repeated debt reflects genuine upstream sparsity rather than maintainer omission.
5. Discovery coverage was still biased toward already-strong optical/CV and boiling-ML areas. The repository needed more targeted search prompts for reduced-order, IR/thermal, and acoustic-emission tooling so future maintenance passes can expand scope where the catalog is currently thin.

## Repetition Compared With 2026-06-25

- Repeated from prior day: yes.
- Recurring issues:
  - dataset paper-link debt still dominates the raw backlog;
  - reduced-order dynamics still remains the weakest mixed paper-plus-license category;
  - the previous audit still lacked a direct mechanism to force attention onto the hardest stale rows.
- Assessment: the June 25 revision improved structural visibility, but it was still insufficient because it stopped at category-level debt. The June 26 pass therefore escalated from summary views to direct row re-verification plus a ranked maintenance frontier.

## Substantive Author-Maintainer Revisions

1. Revised [`data/resources.csv`](../data/resources.csv) after direct source verification:
   - `Deep learning the sound of boiling for advance prediction of boiling crisis` -> changed license from `Archive terms` to verified `CC BY 4.0` from the Mendeley Data page and strengthened notes.
   - `NASA DASHlink incipient boiling dataset` -> strengthened notes to reflect the current public title (`Acoustic and Visual Data for Incipient Boiling at Local Heat Leaks in a Water Tank`), the April 8, 2025 page update, and the continued absence of an exposed license field or linked publication.
   - `BubbleML` -> replaced the paper link with the repository-cited OpenReview record and strengthened notes to reflect what the README actually exposes: documentation, examples, and an open-source claim without a surfaced SPDX-style license file.
   - `BURST`, `Bubble-dynamic`, `Bubble_dynamics_simulation`, and `Bubble_dynamics_simulation_CPP` -> refreshed `source_checked` dates and notes after direct repo re-inspection so the remaining reduced-order and non-boiling bubble-imagery debt is now explicitly documented rather than left implicit.
2. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) to compute a ranked `Priority Maintenance Frontier` based on:
   - issue count per row;
   - total review debt in the row's category;
   - verification age in days.
3. Regenerated [`docs/catalog.md`](../catalog.md), [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and mirrored figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures).
4. Revised [`data/discovery_queries.json`](../../data/discovery_queries.json) to add targeted discovery prompts for:
   - reduced-order bubble dynamics;
   - boiling infrared/thermal tools;
   - acoustic-emission boiling tools.
5. Revised [`README.md`](../../README.md), [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex), and [`paper/arxiv/references.bib`](../../paper/arxiv/references.bib) so the front-page/manuscript framing now reflects the June 26 maintenance logic: direct row rechecks, clarified `sound of boiling` licensing, BubbleML citation normalization to OpenReview, and the new priority-frontier audit concept.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) for the new `Priority Maintenance Frontier` tables and updated license counts
- Checked [`README.md`](../../README.md), [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex), and [`paper/arxiv/references.bib`](../../paper/arxiv/references.bib) for consistency with the new verification findings
- Reconfirmed that manuscript PDF compilation still cannot be verified in this environment because no LaTeX toolchain is installed

## Measured Outcome After This Run

- `Explicit open license` increased from `28` to `29`.
- `Archive/model terms` decreased from `15` to `14`.
- `Manual license review` remained `9`.
- `no paper link` remained `14`; the backlog did not shrink numerically in this run, but its highest-priority rows are now ranked explicitly rather than buried in a flat queue.
- The audit now exposes a row-level maintenance frontier led by:
  - `Two-phase immersion cooler for medium-voltage silicon carbide MOSFETs`
  - `Bubble_dynamics_simulation`
  - `Bubble_dynamics_simulation_CPP`
  - `Pool Boiling Dataset: Synchronized Acoustic, Optical, and Thermal Measurements`
  - `Results of bubble detection and tracking of subcooled boiling flow`

## Unresolved Risks

1. `Bubble_dynamics_simulation` and `Bubble_dynamics_simulation_CPP` still lack both verified licenses and associated paper links after direct rechecking, which suggests the bottleneck may be true upstream sparsity rather than only missed metadata transfer.
2. `Two-phase immersion cooler for medium-voltage silicon carbide MOSFETs` still relies on a Dryad sharing link and lacks a paper link, making it the highest-risk row for future link rot.
3. Stable paper URLs are still missing for several datasets, especially the Harvard Dataverse multimodal pool-boiling dataset, the NASA DASHlink incipient-boiling dataset, the Mendeley `sound of boiling` dataset, the Dryad physical-descriptor dataset, the Dryad transient-hysteresis dataset, and the Mendeley tracking-results archive.
4. `MFiX`, `OpenFOAM interFoam guide`, and `OpenFOAM dispersed multiphase guide` remain the key CFD infrastructure rows with unresolved license-review ambiguity or missing canonical software-paper handling.
5. `BubbleML`, `Boiling Learning`, `BURST`, and the two Zhou optical repos remain the most valuable non-dataset rows still limiting full paper-link or license clarity outside the reduced-order category.
6. Manuscript PDF compilation still cannot be verified in this environment because no LaTeX toolchain is installed.

