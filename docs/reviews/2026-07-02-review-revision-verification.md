# 2026-07-02 Review, Revision, and Verification

## Independent Reviewer Comments

1. The July 1 artifact-type cleanup improved the honesty of the blocker labels, but the ranked maintenance frontier still sent a mixed scientific signal because a less-direct immersion-cooling sharing link could outrank core reduced-order and boiling-specific weaknesses.
2. That is a scope-and-prioritization problem rather than a simple metadata problem. Repeated review effort should land first on direct bubble-dynamics debt, especially the reduced-order rows and boiling datasets with missing paper links, not on transfer-only or peripheral rows.
3. The public-source notes for several dataset-heavy rows were still thinner than they should be. In particular, the Dryad hysteresis and physical-descriptor datasets expose stronger citation text on their landing pages than the catalog previously recorded, and MFiX now exposes a clearer public product description than the older note captured.
4. The manuscript and maintainer guidance still needed to explain how scope alignment affects triage; otherwise future passes could regress by over-focusing on stale but peripheral rows.

## Repetition Compared With 2026-07-01

- Repeated from prior day: yes.
- Recurring issues:
  - reduced-order bubble dynamics remains the weakest mixed paper-plus-license category;
  - dataset paper-link debt still dominates the unresolved queue;
  - the new recurring issue was that the maintenance frontier still overemphasized a peripheral transfer-only row even after artifact-type cleanup.
- Assessment: the July 1 pass fixed false artifact-type debt, but the July 2 reviewer pass showed that ranking logic still needed a deeper scientific-scope revision.

## Substantive Author-Maintainer Revisions

1. Added scope-alignment logic to [`scripts/render_catalog.py`](../../scripts/render_catalog.py) so each active entry is classified as `Core bubble/boiling`, `Adjacent but directly useful`, or `Peripheral or transfer-only`.
2. Extended the renderer to generate a new scope-alignment figure and tables in [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and injected the scope label directly into the manual-review queue and ranked maintenance frontier.
3. Changed frontier scoring so peripheral transfer-only rows are downweighted relative to core bubble-dynamics debt. This moved the reduced-order repos and boiling-specific datasets above the less-direct immersion-cooling sharing-link row.
4. Refreshed direct-source notes plus `source_checked` dates in [`data/resources.csv`](../../data/resources.csv) for:
   - `Unveiling hysteresis of transient boiling: A multimodal perspective`
   - `Generalizable physical descriptors of pool boiling heat transfer from unsupervised learning of images`
   - `MFiX`
5. Revised [`README.md`](../../README.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the human-facing narrative now explains the July 2 scope-alignment revision and its effect on reviewer triage.
6. Regenerated the catalog outputs and mirrored figures, including the new `scope_alignment_by_category` assets under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures).

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) for:
  - new `Scope alignment` counts of `33` core, `17` adjacent, and `3` peripheral rows;
  - a new `scope_alignment_by_category` figure;
  - the `Priority Maintenance Frontier` placing `Bubble_dynamics_simulation`, `Bubble_dynamics_simulation_CPP`, and the NASA DASHlink boiling dataset ahead of the immersion-cooling sharing-link row;
  - updated backfill-ready rows concentrated in `Generalizable physical descriptors...`, `Unveiling hysteresis...`, and `MFiX`.
- Direct source verification used during this pass:
  - Dryad page for `Generalizable physical descriptors of pool boiling heat transfer from unsupervised learning of images`, whose abstract and README now publicly expose the IJHMT citation text `(255, 2026, 127894)`;
  - Dryad page for `Unveiling hysteresis of transient boiling: A multimodal perspective`, whose public title and abstract are stronger than the older note captured;
  - official NETL MFiX product page, which now publicly describes MFiX as an open-source suite with theory-guide and citations-database links.
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment.

## Measured Outcome After This Run

- The maintenance frontier is now more scientifically focused: direct reduced-order and boiling-specific debt ranks ahead of peripheral transfer-only rows.
- The generated documentation now makes scope alignment explicit instead of leaving users to infer it from notes.
- Three rows remain in the backfill-ready queue, but they are now a tighter and more defensible set than the broader, less-focused frontier from the prior run.

## Unresolved Risks

1. Reduced-order bubble dynamics still has the weakest combined paper-link and license clarity.
2. Several dataset rows still expose public citation text without a stable article URL or DOI link, so the remaining backfill queue is not fully resolved.
3. The immersion-cooling dataset still relies on a review-sharing link and remains a long-term access/stability risk even after being downweighted.
4. The Harvard Dataverse multimodal boiling dataset remains JavaScript-gated in this environment and still lacks a stable associated paper URL from repeated public checks.
5. Manuscript PDF compilation still cannot be validated in this environment because no LaTeX toolchain is installed.
