# 2026-07-01 Review, Revision, and Verification

## Independent Reviewer Comments

1. The June 30 false-backfill fix improved the queue, but one structural problem remained: documentation pages, thesis-style research repositories, and a JavaScript-gated dataset landing page were still being treated as if they were ordinary maintainer metadata debt.
2. That classification still overstated what the maintainers could realistically fix inside this repository. Repeated comments about `Boiling Learning`, the OpenFOAM guide rows, and the Harvard Dataverse multimodal dataset were now evidence that the remaining issue was public discoverability and artifact type, not shallow CSV incompleteness.
3. The CFD/documentation layer needed a clearer policy distinction between a guide page that belongs to a licensed parent software project and a standalone code artifact that should expose its own explicit reuse terms.
4. The manuscript and maintainer guidance still needed to state that distinction directly, otherwise future passes would keep recreating the same false maintainer queue even after multiple source checks.

## Repetition Compared With 2026-06-30

- Repeated from prior day: yes.
- Recurring issues:
  - dataset-heavy paper-link debt still dominates the unresolved queue;
  - reduced-order dynamics still remains structurally weak;
  - the sharper recurring issue was still false fixability, now concentrated in `Boiling Learning`, the OpenFOAM guide rows, and the Harvard Dataverse multimodal dataset.
- Assessment: the June 30 pass fixed several false-backfill rows, but the recurrence itself showed the remaining queue still needed a deeper artifact-type and public-discoverability revision rather than another round of shallow source checks.

## Substantive Author-Maintainer Revisions

1. Refreshed direct-source notes and `source_checked` dates in [`data/resources.csv`](../../data/resources.csv) for:
   - `Pool Boiling Dataset: Synchronized Acoustic, Optical, and Thermal Measurements`
   - `Boiling Learning`
   - `OpenFOAM interFoam guide`
   - `OpenFOAM dispersed multiphase guide`
2. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) with a documentation-license-context rule so documentation rows linked to a licensed parent project are no longer automatically flagged as standalone `license check` debt.
3. Tightened blocker classification so notes about absent public thesis/paper URLs or JavaScript-gated citation discoverability are treated as `upstream sparsity` instead of lingering in false `catalog backfill`.
4. Regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and mirrored figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures).
5. Revised [`README.md`](../../README.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the human-facing narrative now explains the July 1 documentation-policy and discoverability reclassification.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/reproducibility_audit.md`](../reproducibility_audit.md) and [`docs/summary.md`](../summary.md) for:
  - `catalog backfill = 0`;
  - `upstream sparsity = 16`;
  - CFD license clarity improving from `8/11` to `10/11`;
  - the `Backfill-Ready Queue` becoming empty rather than continuing to recycle the same rows.
- Direct source verification used during this pass:
  - GitHub repository page for `ruancomelli/boiling-learning`
  - OpenFOAM Foundation dispersed multiphase guide page
  - OpenFOAM Foundation GPL license page
  - Harvard Dataverse landing page for `doi:10.7910/DVN/6GLGC6`, which still required JavaScript verification in this environment
  - repeated title- and DOI-based web searches for the Harvard Dataverse multimodal dataset, which still did not surface a stable associated paper URL
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment.

## Measured Outcome After This Run

- The false-maintainer queue is now eliminated: the generated `Backfill-Ready Queue` is empty.
- The remaining unresolved debt is now explicitly partitioned as either:
  - `upstream sparsity` for absent public paper/license/thesis evidence; or
  - `access/link stability` for the Dryad review-sharing row.
- CFD and multiphase simulation now shows only one unresolved blocker (`MFiX`) instead of three, because the OpenFOAM guide rows are no longer misframed as standalone license debt.

## Unresolved Risks

1. Dataset paper-link debt is still the largest unresolved class, even though it is now more honestly labeled as upstream-limited.
2. Reduced-order bubble dynamics remains the weakest category on combined paper-link and license clarity.
3. The Dryad sharing-link row for the two-phase immersion cooler dataset remains an access and long-term stability risk.
4. The Harvard Dataverse multimodal dataset still has unresolved public citation discoverability because the landing page is JavaScript-gated in this environment and no stable paper URL was surfaced by repeated search.
5. Manuscript PDF compilation still cannot be validated in this environment because no LaTeX toolchain is installed.
