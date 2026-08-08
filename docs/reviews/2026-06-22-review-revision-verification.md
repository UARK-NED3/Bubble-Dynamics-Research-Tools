# 2026-06-22 Review, Revision, and Verification

## Independent Reviewer Comments

1. The previous two runs identified metadata debt as the dominant bottleneck, and that critique was still valid at the start of this run. Entire categories looked weaker than they really were because canonical software citations for baseline utilities and solver infrastructure were missing from the catalog.
2. General image and flow utilities were the clearest example of under-curation-by-omission: scikit-image, Fiji, napari, and Trackpy are standard workflow building blocks, but the repo had treated them as uncited links rather than traceable research software.
3. Reduced-order dynamics still looked especially fragile. Even after the June 21 pass, the category had `0%` paper-link coverage and poor license clarity, which made the audit overstate uncertainty for tutorial and verification resources.
4. CFD and multiphase coverage still lagged the manuscript narrative. The paper cited canonical solver references, but the CSV and generated audit did not consistently expose those links back to users.
5. The manuscript argument had improved over prior days, but it still needed a more explicit explanation that some prior audit weakness came from missing catalog metadata on established baseline tools, not only from weak upstream projects.
6. Reproducibility is still limited by the environment: the manuscript PDF cannot be compiled here until a LaTeX toolchain is available.

## Repetition Compared With 2026-06-21

- Repeated from prior day: yes.
- Recurring issue: metadata debt remained the main critique, especially missing paper links in reduced-order, CFD, and utility categories.
- Assessment: the June 21 revision improved the dashboard but did not directly backfill enough canonical citations, so a deeper source-verification pass was warranted.

## Substantive Author-Maintainer Revisions

1. Backfilled canonical citation metadata in [`data/resources.csv`](../data/resources.csv) for high-impact baseline tools and solver infrastructure:
   - `scikit-image` -> PeerJ paper DOI
   - `ImageJ/Fiji` -> Nature Methods paper DOI and explicit `GPL`
   - `napari` -> Zenodo software DOI
   - `Trackpy` -> official citation page in Trackpy docs
   - `Basilisk` and `Basilisk Rayleigh-Plesset test` -> canonical Basilisk solver paper DOI
   - `Bubble-dynamic` -> repository-hosted single-bubble dynamics PDF
   - `bubble-dynamics-resnet` -> verified `MIT` license from the upstream repository
2. Revised [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) to make the metadata-repair rationale explicit and to better frame baseline utilities as part of the practical bubble-analysis stack rather than peripheral extras.
3. Expanded [`paper/arxiv/references.bib`](../../paper/arxiv/references.bib) with a formal Fiji citation and a DOI-backed napari software citation, and aligned the Trackpy bibliography entry with the official citation guidance page.
4. Updated [`README.md`](../../README.md) so the repo front page reflects the stronger citation coverage and points future maintenance toward the remaining true weak spots instead of the already-fixed utility gap.
5. Regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), [`docs/catalog.md`](../catalog.md), and the figure set under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures).

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Inspected regenerated summary/audit outputs for category-level movement

## Measured Outcome After This Run

- `Partial link coverage` decreased from `33` to `27`.
- `Code + paper/docs` increased from `5` to `11`.
- `Explicit open license` increased from `21` to `23`.
- `General image and flow utilities` paper-link coverage increased from `0%` to `57%`.
- `Reduced-order bubble dynamics` paper-link coverage increased from `0%` to `40%`.
- `CFD and multiphase simulation` paper-link coverage increased from `9%` to `18%`.

## Unresolved Risks

1. Reduced-order dynamics still has two tutorial/code repos without verified licenses or paper links: `Bubble_dynamics_simulation` and `Bubble_dynamics_simulation_CPP`.
2. CFD and multiphase still has weak paper-link depth for `OpenFOAM`, `Aphros`, `FluidX3D`, `JumpingBubbles`, `MFiX`, `Outflow-Forcing-BubbleML`, and the viscoelastic Worthington-jet repo.
3. `PIVlab` still lacks an explicit license and canonical citation in the catalog.
4. Several optical-imaging and dataset entries still need direct paper-link backfill or upstream license verification.
5. Manuscript PDF compilation was not verified in this environment because no LaTeX toolchain is available.
