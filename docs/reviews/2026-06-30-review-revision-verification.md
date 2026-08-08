# 2026-06-30 Review, Revision, and Verification

## Independent Reviewer Comments

1. The queue-structure improvement from June 29 was necessary but not sufficient. Several rows still appeared in the `Backfill-Ready Queue` even though direct inspection of the public source pages suggested the missing evidence was not currently exposed upstream.
2. Repeated critique remained concentrated in dataset paper-link debt and generic-license handling, but the more precise issue was false fixability: the repository still implied some rows should be easy maintainer edits when they were actually blocked by absent public license files or absent public paper links.
3. Row notes for several frontier entries had become too generic to support that distinction. Without source-specific notes, the same rows were likely to recur again tomorrow under the wrong blocker type.
4. Manuscript and maintainer guidance needed to reflect this sharper interpretation of debt so future passes do not keep rechecking upstream-limited rows as if they were ordinary metadata transfer work.

## Repetition Compared With 2026-06-29

- Repeated from prior day: yes.
- Recurring issues:
  - dataset-heavy paper-link debt still dominates the remaining review queue;
  - reduced-order dynamics still remains structurally weak;
  - some rows were still being treated as `catalog backfill` even after repeated passes should have triggered a deeper direct-source verification.
- Assessment: the June 29 pass correctly separated backlog classes, but today confirmed that several recurring frontier rows belonged in `upstream sparsity`, not in the maintainer-action queue. That made a deeper source-verification revision necessary.

## Substantive Author-Maintainer Revisions

1. Refreshed direct-source notes and `source_checked` dates in [`data/resources.csv`](../../data/resources.csv) for five recurring frontier rows:
   - `Deep learning the sound of boiling for advance prediction of boiling crisis`
   - `BubbleML`
   - `Bubble detection and tracking AI-based YOLO tracking algorithm`
   - `Robust TH analysis method for bubbles using AI`
   - `bubble-dynamics-resnet`
   - plus a fresh direct-source note update for `OpenFOAM dispersed multiphase guide`
2. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) so blocker classification now treats explicit note signals such as missing public license files, missing public paper links, and missing software citations as `upstream sparsity` rather than leaving those rows in false `catalog backfill`.
3. Regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and mirrored figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures). The key measurable change is that true `catalog backfill` dropped from `10` rows to `4`, while `upstream sparsity` rose to `14`, making the remaining maintainable queue much more honest.
4. Revised [`README.md`](../../README.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the human-facing narrative now explains the June 30 direct-source reclassification and instructs maintainers to stop treating absent public license or paper evidence as routine metadata transfer.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) for:
  - blocker counts changing from `catalog backfill = 10` / `upstream sparsity = 8` to `catalog backfill = 4` / `upstream sparsity = 14`;
  - Zhou repositories, `BubbleML`, `bubble-dynamics-resnet`, and the Mendeley `sound of boiling` dataset moving out of the backfill-ready queue;
  - consistent frontier tables and mirrored figure outputs.
- Direct source verification used during this pass:
  - GitHub repository page for `zhouzhouwen/Bubble_detection_and_tracking_AI_based_YOLO_tracking_alogrithm`
  - GitHub repository page for `zhouzhouwen/The-Robust-Development-of-a-TH-Analysis-Method-for-Bubbles-Using-AI`
  - GitHub repository page for `HPCForge/BubbleML`
  - GitHub repository page for `comp-physics/bubble-dynamics-resnet`
  - Mendeley Data page for `Deep learning the sound of boiling for advance prediction of boiling crisis`
  - OpenFOAM Foundation guide page for dispersed multiphase flows
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment.

## Measured Outcome After This Run

- The remaining `Backfill-Ready Queue` now contains only four rows:
  - `Pool Boiling Dataset: Synchronized Acoustic, Optical, and Thermal Measurements`
  - `OpenFOAM interFoam guide`
  - `Boiling Learning`
  - `OpenFOAM dispersed multiphase guide`
- The previously recurring Zhou repositories, `BubbleML`, `bubble-dynamics-resnet`, and the Mendeley `sound of boiling` dataset no longer overstate maintainability; they are now documented as upstream-limited.
- Reduced-order bubble dynamics now shows `0` catalog-backfill issues and `4` upstream-sparsity issues, which is a more defensible description of that category's remaining weakness.

## Unresolved Risks

1. The Harvard Dataverse multimodal pool-boiling dataset remains the highest-leverage dataset row that still appears genuinely backfillable.
2. The OpenFOAM documentation-guide rows still need a firmer, policy-consistent interpretation of documentation-page license evidence versus software-license evidence.
3. The Dryad sharing-link row for the two-phase immersion cooler dataset remains an access/link-stability risk.
4. Several reduced-order repositories still appear to be genuinely upstream-sparse rather than cleanable from within this repository.
5. Manuscript PDF compilation still cannot be validated in this environment because no LaTeX toolchain is installed.
