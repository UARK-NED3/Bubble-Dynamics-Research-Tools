# 2026-07-03 Review, Revision, and Verification

## Independent Reviewer Comments

1. The July 2 scope-aware frontier fixed a real scientific-prioritization problem, but the remaining dataset debt was still too coarse. The audit continued to treat citation-verified Dryad rows and the MFiX citations-database case as if they were equivalent to rows with no public paper evidence at all.
2. That coarseness matters because it can trigger repeated low-yield maintenance passes. A curator should not keep rechecking the same Dryad landing page once the title-level citation evidence is already confirmed and the only missing artifact is a canonical article URL or DOI on the public page.
3. The repository therefore still needed a stronger paper-evidence model, not just more row-by-row note edits. Without that change, the summary tables, blocker logic, and maintenance frontier would keep overstating backfill-ready debt in the datasets category.
4. After that classification fix, the scientifically strongest remaining weaknesses are clearer: reduced-order bubble-dynamics repositories still have the weakest combined license-plus-paper evidence, and several datasets still have genuinely unresolved paper discoverability rather than merely unresolved URLs.

## Repetition Compared With 2026-07-02

- Repeated from prior day: yes.
- Recurring issues:
  - dataset paper-link debt still dominated the unresolved queue;
  - the Dryad hysteresis and physical-descriptor rows still appeared as maintainer-owned paper-link debt even after direct source notes had already been strengthened;
  - MFiX still sat in the backfill-ready queue despite the public site already exposing only project-level citation evidence rather than a canonical software-paper URL.
- Assessment: the July 2 pass improved scientific prioritization, but today’s repeated critique showed that the repo still needed a deeper classification revision so citation-verified rows would stop masquerading as easy backfill.

## Substantive Author-Maintainer Revisions

1. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) with a paper-evidence model that distinguishes:
   - direct paper links;
   - citation text verified but URL unresolved;
   - project citation database only;
   - no public paper evidence surfaced.
2. Changed the audit logic so unresolved citation discoverability is tracked separately from `catalog backfill` and `upstream sparsity`, and split review debt into `no paper evidence` versus `paper URL unresolved`.
3. Added a new `paper_evidence_by_category` figure and expanded the metadata-coverage figure so category summaries now show both direct paper-link coverage and any verified paper evidence.
4. Refreshed the source notes plus `source_checked` dates in [`data/resources.csv`](../../data/resources.csv) for:
   - `Generalizable physical descriptors of pool boiling heat transfer from unsupervised learning of images`
   - `Unveiling hysteresis of transient boiling: A multimodal perspective`
   - `MFiX`
5. Revised [`README.md`](../../README.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the human-facing narrative now explains the July 3 citation-evidence revision and tells maintainers when to stop treating a row as easy backfill.
6. Regenerated the catalog outputs and mirrored figures, including the new `paper_evidence_by_category` assets under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures).

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) for:
  - `Paper evidence` counts of `30` direct paper links, `2` citation-verified URL-unresolved rows, `1` project-citation-only row, and `10` rows with no public paper evidence surfaced;
  - a new `paper_evidence_by_category` figure;
  - datasets improving from `6/12` direct paper links to `8/12` rows with any verified paper evidence;
  - the Dryad physical-descriptor row, Dryad hysteresis row, and MFiX moving from implied backfill into explicit `citation discoverability`;
  - an empty `Backfill-Ready Frontier`, which is the intended result after removing the false backfill classification rather than evidence of a clean catalog.
- Direct source verification relied on the publicly visible Dryad notes already recorded during July 2, plus the official MFiX product-page/citations-database description now encoded more explicitly in the catalog note.
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment.

## Measured Outcome After This Run

- The repo no longer conflates citation-verified rows with genuinely uncited rows.
- The repeated Dryad/MFiX critique is now resolved at the schema-and-audit level rather than hidden by another note-only pass.
- The remaining highest-priority debt is more honest and more scientifically useful: reduced-order code evidence and genuinely unresolved dataset paper discoverability now dominate the frontier.

## Unresolved Risks

1. Reduced-order bubble dynamics still has the weakest combined paper-link and license clarity, especially `Bubble_dynamics_simulation` and `Bubble_dynamics_simulation_CPP`.
2. Several datasets still have no public paper evidence surfaced at all, especially the NASA DASHlink incipient-boiling row, the Harvard Dataverse multimodal row, and the Mendeley `sound of boiling` row.
3. The immersion-cooling sharing-link row remains an access-stability risk even after being downweighted for scope.
4. MFiX still lacks a public SPDX-style license statement and a single canonical software-paper URL even though project-level citation evidence is now encoded correctly.
5. Manuscript PDF compilation still cannot be validated in this environment because no LaTeX toolchain is installed.
