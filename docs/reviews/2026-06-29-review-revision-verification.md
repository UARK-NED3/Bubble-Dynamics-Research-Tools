# 2026-06-29 Review, Revision, and Verification

## Independent Reviewer Comments

1. The main recurring weakness after the June 28 license fix is no longer misclassification of restrictive licenses; it is that the repository still mixes two very different kinds of unresolved debt in one queue. Repeated comments about paper-link and license gaps are hard to close decisively when solvable catalog backfill sits beside rows whose upstream sources still do not expose stronger evidence.
2. Dataset curation remains the largest structural risk. The audit shows that datasets still dominate missing paper-link debt, but the previous outputs did not make it obvious which dataset rows should change after a deeper maintainer pass versus which ones are currently capped by archive-side metadata sparsity.
3. Repo usability for maintainers needed a stronger operational path. The priority frontier was useful, but it still forced a human to mentally filter out upstream-sparse rows before deciding what to edit. That leaves too much room for another shallow pass that simply rechecks the same hard rows.
4. Several row notes were aging into generic summaries. The catalog needed fresh direct-source notes for at least some backfill-ready rows or infrastructure-adjacent entries so the manuscript and docs would reflect current evidence rather than only older descriptions.

## Repetition Compared With 2026-06-28

- Repeated from prior day: yes.
- Recurring issues:
  - dataset-heavy paper-link debt still dominates the remaining maintenance frontier;
  - reduced-order dynamics still remains a stubborn weak category because several rows appear to be limited by genuine upstream sparsity;
  - the repository still needed a better way to separate solvable maintainer backfill from unresolved upstream evidence ceilings.
- Assessment: the June 28 pass correctly fixed the license-overstatement bug, but it did not yet make the next maintainer action obvious enough. Another day of flat-queue triage would likely have repeated the same critiques without materially improving maintainability.

## Substantive Author-Maintainer Revisions

1. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) so the generated outputs now separate blocker type by workflow category and expose a filtered backfill queue:
   - added blocker-by-category aggregation;
   - added `review_blockers_by_category` figures in SVG, PNG, and PDF;
   - added `Review Blockers By Category` tables to the summary and reproducibility audit;
   - added `Backfill-Ready Frontier` / `Backfill-Ready Queue` sections filtered to `catalog backfill` rows.
2. Refreshed direct-source notes in [`data/resources.csv`](../../data/resources.csv):
   - `Boiling Learning` now records the public GPL-3.0 license signal, UFSC master's-project context, and the presence of tests/changelog/release activity from the repository page;
   - `OpenFOAM dispersed multiphase guide` now records that the guide consolidates dispersed-flow solver context and that the exact page footer links the OpenFOAM GPLv3 software license, while still treating the guide itself as documentation.
3. Regenerated [`docs/catalog.md`](../catalog.md), [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and mirrored figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures) so the blocker split and filtered queue propagate everywhere the catalog is consumed.
4. Revised [`README.md`](../../README.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) to explain the new blocker-oriented maintenance logic, update the current maintenance date, and document how recurring critiques should now be handled.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) for:
  - presence of the new blocker-by-category figure and tables;
  - correct separation of `catalog backfill`, `upstream sparsity`, and `access/link stability`;
  - correct filtered backfill queue entries.
- Confirmed new figure artifacts were written to [`figures/review_blockers_by_category.svg`](../../figures/review_blockers_by_category.svg), [`figures/review_blockers_by_category.png`](../../figures/review_blockers_by_category.png), and [`figures/review_blockers_by_category.pdf`](../../figures/review_blockers_by_category.pdf).
- Direct source verification used during this pass:
  - GitHub repository page for `ruancomelli/boiling-learning`
  - OpenFOAM Foundation guide page for `disperse multiphase flows`
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment.

## Measured Outcome After This Run

- The generated audit now makes the highest-leverage maintainable queue explicit instead of leaving reviewers to infer it from the flat frontier.
- `catalog backfill` is now isolated as `10` issues, with category concentrations visible directly:
  - Datasets: `2`
  - Optical imaging and computer vision: `3`
  - Reduced-order bubble dynamics: `1`
  - CFD and multiphase simulation: `2`
  - Simulation and ML benchmarks: `2`
- The filtered backfill queue now surfaces concrete next-pass targets such as the Harvard Dataverse multimodal pool-boiling dataset, `bubble-dynamics-resnet`, the Zhou repositories' license handling, and OpenFOAM documentation-license interpretation without mixing them with clearly upstream-sparse rows.
- Boiling Learning and the OpenFOAM dispersed-flow guide now have fresher, more source-specific notes and `source_checked = 2026-06-29`.

## Unresolved Risks

1. The highest-ranked frontier row remains `Two-phase immersion cooler for medium-voltage silicon carbide MOSFETs`, but it is still limited by a Dryad sharing link and no surfaced paper link.
2. Reduced-order rows `Bubble_dynamics_simulation`, `Bubble_dynamics_simulation_CPP`, and `Bubble-dynamic` still look like genuine upstream sparsity rather than easy catalog cleanup.
3. Dataset paper-link debt remains substantial even after the new queue split; the Harvard Dataverse multimodal boiling dataset and the Mendeley `sound of boiling` dataset remain the clearest backfill-ready targets for a future pass.
4. `BubbleML`, `OpenFOAM interFoam guide`, and the two Zhou repositories still need direct license-resolution work if future maintenance time is spent on solvable catalog backfill.
5. Manuscript PDF compilation still cannot be validated in this environment because no LaTeX toolchain is installed.
