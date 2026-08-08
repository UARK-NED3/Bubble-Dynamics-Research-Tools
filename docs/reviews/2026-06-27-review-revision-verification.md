# 2026-06-27 Review, Revision, and Verification

## Independent Reviewer Comments

1. The same central critique still repeated from prior runs at the start of this pass: the catalog no longer has diffuse metadata debt, but it still contains a recurring frontier of unresolved rows. A stronger revision needed to close at least one high-priority row outright rather than only improving prioritization around it.
2. The dataset backlog was still being treated too uniformly. Some rows were clearly missing maintainers' metadata transfer, while others had already been rechecked repeatedly and still lacked upstream paper or license evidence. Without that distinction, repeated comments risk overstating maintainer omission where the real issue is upstream sparsity.
3. Discovery workflow remained structurally biased toward GitHub repositories even though the heaviest remaining debt is in datasets and archive-first resources. The repository needed discovery infrastructure that explicitly keeps Dryad, Mendeley Data, Dataverse, Hugging Face, NASA DASHlink, and similar sources in view.
4. The Mendeley tracking-results archive had become a good test case for whether the review loop was actually resolving recurring debt. Its public page already exposed a concrete CC BY 4.0 license and linked the associated repository, so leaving it unresolved another day would have been evidence that prior revisions were still too shallow.

## Repetition Compared With 2026-06-26

- Repeated from prior day: yes.
- Recurring issues:
  - dataset paper-link debt still dominates the remaining queue;
  - reduced-order dynamics still remains the weakest mixed paper-plus-license category;
  - recurring comments were still not cleanly separating maintainer-backfill debt from genuine upstream sparsity.
- Assessment: the June 26 revision was directionally useful but still insufficient. Ranking the frontier made the backlog visible, but one more deeper pass was needed to close a frontier row directly and to explain why some stubborn rows remain unresolved after repeated rechecks.

## Substantive Author-Maintainer Revisions

1. Revised [`data/resources.csv`](../data/resources.csv) after direct source verification:
   - `Results of bubble detection and tracking of subcooled boiling flow` -> replaced `Archive terms` with verified `CC BY 4.0` from the Mendeley Data page, added the linked `https://doi.org/10.1016/j.ijmultiphaseflow.2025.105246` paper, and strengthened the notes to explain why the association is defensible from the archive description itself.
2. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) so the generated summary and audit now classify unresolved rows by blocker type:
   - `catalog backfill` for rows that still look solvable by maintainer transfer;
   - `upstream sparsity` for rows whose public source still does not expose stronger citation or license evidence after direct rechecking;
   - `access/link stability` for review-sharing or similarly fragile archive links.
3. Extended [`scripts/discover_candidates.py`](../../scripts/discover_candidates.py) so the generated discovery report now includes:
   - `Manual Web Search Seeds`;
   - `Manual Archive Search Seeds`.
   This directly addresses the recurring discovery bias toward GitHub-visible code when current debt is concentrated in archive-hosted datasets.
4. Regenerated [`docs/catalog.md`](../catalog.md), [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), mirrored figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures), and refreshed [`docs/discovery_candidates.md`](../discovery_candidates.md).
5. Revised [`README.md`](../../README.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the repo front page, curation guidance, and manuscript now reflect the June 27 maintenance logic: one frontier row closed, blocker-type separation added, and archive-first discovery made explicit.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/discover_candidates.py --output docs/discovery_candidates.md`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), [`docs/catalog.md`](../catalog.md), and [`docs/discovery_candidates.md`](../discovery_candidates.md) for consistency with the revised row metadata and blocker-type logic
- Reconfirmed that GitHub network access remains blocked in this environment, so the discovery report currently records failed GitHub API fetches while still emitting the manual web/archive search seeds
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment

## Measured Outcome After This Run

- `Code + data + paper` increased from `17` to `18`.
- `Partial link coverage` decreased from `16` to `15`.
- `Explicit open license` increased from `29` to `30`.
- `Archive/model terms` decreased from `14` to `13`.
- `no paper link` decreased from `14` to `13`.
- `Datasets` review debt decreased from `8` total issues to `7`.
- The generated audit now distinguishes unresolved debt by blocker type:
  - `10` `catalog backfill`
  - `8` `upstream sparsity`
  - `1` `access/link stability`
- `Results of bubble detection and tracking of subcooled boiling flow` no longer appears in the manual-review queue or the ranked priority frontier.

## Unresolved Risks

1. `Bubble_dynamics_simulation` and `Bubble_dynamics_simulation_CPP` remain the clearest repeated-review rows in reduced-order dynamics; current evidence suggests genuine upstream sparsity rather than simple catalog omission.
2. `Two-phase immersion cooler for medium-voltage silicon carbide MOSFETs` remains the highest-risk dataset row because it still depends on a Dryad sharing link and lacks an associated paper link.
3. The remaining dataset backlog is smaller but still consequential: stable paper URLs are still missing for Harvard Dataverse multimodal pool boiling, NASA DASHlink incipient boiling, the Mendeley `sound of boiling` dataset, the Dryad physical-descriptor dataset, and the Dryad transient-hysteresis dataset.
4. `MFiX`, `OpenFOAM interFoam guide`, and `OpenFOAM dispersed multiphase guide` remain the key CFD infrastructure rows where canonical citation or license treatment still needs either stronger source evidence or a stricter maintainer policy.
5. GitHub API access is blocked in this environment, so discovery automation cannot currently validate live repository search results even though the report now preserves archive/web search seeds for manual follow-up.
6. Manuscript PDF compilation still cannot be verified in this environment because no LaTeX toolchain is installed.
