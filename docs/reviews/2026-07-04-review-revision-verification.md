# 2026-07-04 Review, Revision, and Verification

## Independent Reviewer Comments

1. The July 3 paper-evidence revision fixed the repeated Dryad/MFiX misclassification, but the next recurring weakness was now exposed more clearly: reduced-order bubble-dynamics entries were still presented mostly as a deficit list rather than as an actionable adoption ladder for users deciding what to trust first.
2. That gap matters scientifically and practically. The reduced-order category contains materially different artifacts: a reference-backed Basilisk verification case, a pedagogical Bubble-dynamic repository with a bundled paper, and two kozakaron simulation repositories that remain prototype-like because their public pages still lack explicit licensing and scholarly citation metadata.
3. The repository’s discovery workflow also remained weaker than it should be under the current environment. `scripts/discover_candidates.py` degraded into repeated socket errors when GitHub API access was blocked, which made the generated discovery report much less useful for maintainers despite the repo’s explicit daily-review workflow.
4. Several row notes still needed refreshed source-verification phrasing so the blocker model would keep classifying true upstream evidence gaps as `upstream sparsity` instead of accidentally falling back to maintainer-owned backfill.

## Repetition Compared With 2026-07-03

- Repeated from prior day: yes.
- Recurring issues:
  - reduced-order bubble dynamics remained the weakest mixed paper-plus-license category;
  - the frontier still lacked enough row-level guidance for users to distinguish reference anchors from pedagogical or prototype single-bubble code;
  - a new maintainability issue became explicit today: the discovery report was not robust when live GitHub search was blocked in this environment.
- Assessment: the July 3 pass resolved the prior repeated dataset-classification critique, but today’s repeated reduced-order weakness showed that the repo still needed a deeper usability and curation-logic revision rather than another row-note-only pass.

## Substantive Author-Maintainer Revisions

1. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) with a reduced-order readiness model and generated `Reduced-Order Snapshot` / `Reduced-Order Triage` tables in the summary and reproducibility audit. The reduced-order layer is now rendered as `Reference-backed`, `Paper-backed, license unclear`, `Code-backed, paper sparse`, or `Prototype-only` instead of as a single weak bucket.
2. Refreshed source-verified catalog rows in [`data/resources.csv`](../../data/resources.csv) for:
   - `Bubble-dynamic`, whose bundled PDF was matched to the canonical arXiv preprint `Modeling the dynamics of single-bubble sonoluminescence`;
   - `Bubble_dynamics_simulation`;
   - `Bubble_dynamics_simulation_CPP`;
   - `Deep learning the sound of boiling for advance prediction of boiling crisis`.
3. Revised [`scripts/discover_candidates.py`](../../scripts/discover_candidates.py) so the generated discovery report remains actionable when GitHub API calls are blocked. The report now:
   - explains the network restriction cleanly instead of repeating raw socket failures without guidance;
   - adds a `Gap-Targeted Priorities` section derived from the current catalog itself;
   - keeps discovery useful for repeated-maintenance runs even when live repository search is unavailable.
4. Expanded [`data/discovery_queries.json`](../../data/discovery_queries.json) with more targeted reduced-order, sonochemistry, MFiX, and archive search prompts so future discovery work is less biased toward already-strong optical categories.
5. Revised [`README.md`](../../README.md), [`docs/quickstart.md`](../quickstart.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the human-facing narrative now explains the July 4 reduced-order triage revision, the recovered Bubble-dynamic paper link, and the new offline-safe discovery workflow.
6. Regenerated the catalog outputs and mirrored figures/documentation so the rendered repo state matches the updated CSV and renderer logic.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- `python scripts/discover_candidates.py --output docs/discovery_candidates.md`
- Checked regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), [`docs/discovery_candidates.md`](../discovery_candidates.md), and [`README.md`](../../README.md) for:
  - the new `Reduced-Order Snapshot` and `Reduced-Order Triage` sections;
  - `Bubble-dynamic` moving from a bundled GitHub PDF link to a canonical arXiv paper URL while retaining a clear manual-license-review warning;
  - blocker counts returning the kozakaron rows and the `sound of boiling` dataset to explicit `upstream sparsity` rather than false `catalog backfill`;
  - the discovery report’s new `Gap-Targeted Priorities` section and cleaner offline-search messaging;
  - manuscript date and narrative updates reflecting the July 4 pass.
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment.

## Measured Outcome After This Run

- The repeated reduced-order critique is now addressed at the renderer and documentation level rather than hidden inside another generic weak-category statement.
- Users can now distinguish which reduced-order entries are safer scientific anchors and which are still mostly pedagogical or prototype code.
- The discovery workflow is materially more maintainable in this environment because blocked GitHub API calls no longer leave the generated report functionally empty.

## Unresolved Risks

1. The two kozakaron reduced-order repositories still lack explicit public license files and associated paper links, so they remain scientifically interesting but reuse-risky.
2. Several dataset rows still have genuinely unresolved paper discoverability or absent public paper evidence, especially the NASA DASHlink incipient-boiling row, the Harvard Dataverse multimodal row, and the Mendeley `sound of boiling` row.
3. Bubble-dynamic is now better anchored by a canonical paper link, but its public repository still lacks an explicit license file, so downstream reuse rights remain unclear.
4. The immersion-cooling sharing-link dataset remains an access-stability risk even after being downweighted for scope.
5. Manuscript PDF compilation still cannot be validated in this environment because no LaTeX toolchain is installed.
