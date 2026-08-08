# 2026-06-28 Review, Revision, and Verification

## Independent Reviewer Comments

1. A repeated weakness remained from prior runs even after the blocker-type split: the audit still conflated reuse clarity with openness. By treating restrictive Creative Commons variants as effectively open, the repository risked overstating downstream reuse rights for technically strong but policy-constrained rows.
2. The recurring dataset critique was no longer only about missing paper links. The stronger concern was that archive-hosted resources with explicit but restrictive terms were being counted too favorably relative to truly open data and code.
3. The Simulation and ML benchmarks and Scientific machine learning sections needed a sharper distinction between `open/permissive` and `explicit restrictive` resources. Without that separation, users could misread NUCLEUS or similar rows as interchangeable with MIT- or GPL-licensed artifacts.
4. FluidVerse had become a concrete test case for whether the catalog would transfer visible archive metadata into the CSV after repeated review pressure. Its public Hugging Face dataset card already exposed `cc-by-nc-4.0`, so leaving it under generic dataset terms would have been another shallow pass.

## Repetition Compared With 2026-06-27

- Repeated from prior day: yes.
- Recurring issues:
  - dataset-heavy maintenance debt still dominates the frontier;
  - reduced-order dynamics still remains the weakest mixed paper-plus-license category;
  - prior revisions improved queue structure but still did not fully correct how reuse rights were being represented.
- Assessment: the June 27 revision was useful but insufficient. Separating `catalog backfill` from `upstream sparsity` improved the maintenance logic, yet the generated outputs still overstated openness for some explicitly restrictive rows. This pass needed a renderer-level correction, not another prose-only clarification.

## Substantive Author-Maintainer Revisions

1. Revised [`data/resources.csv`](../data/resources.csv) after direct source verification:
   - `FluidVerse 2D shock-induced air bubble collapse in water` -> replaced generic `Dataset terms` with verified `CC BY-NC 4.0` from the public Hugging Face dataset card, refreshed the notes to record the visible ALPACA metadata/download guidance, and updated `source_checked` to `2026-06-28`.
2. Corrected [`scripts/render_catalog.py`](../../scripts/render_catalog.py) so generated outputs no longer misclassify restrictive Creative Commons terms as open:
   - `CC BY`, `CC BY-SA`, and `CC0` now count as `Explicit open license`;
   - `CC BY-NC`, `CC BY-ND`, and `CC BY-NC-ND` now count as `Explicit restrictive terms`;
   - category coverage tables now report both `Open/permissive` and `Explicit restrictive` counts rather than collapsing them into a single license signal.
3. Regenerated [`docs/catalog.md`](../catalog.md), [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and mirrored figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures) so the revised license logic propagates everywhere the catalog is consumed.
4. Revised [`README.md`](../../README.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the repository front page, curation policy, and manuscript now explain that restrictive Creative Commons terms are explicit but not equivalent to open-source reuse.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Checked regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and [`docs/catalog.md`](../catalog.md) for consistency with the revised license classifier
- Direct source verification used during this pass:
  - Mendeley Data page for `Deep learning the sound of boiling for advance prediction of boiling crisis`
  - Hugging Face dataset card for `FluidVerse/2D_SABW_SSOO`
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment

## Measured Outcome After This Run

- `Explicit open license` decreased from `30` to `29`, but this reflects stricter classification rather than a loss of resources.
- `Archive/model terms` decreased from `13` to `12`.
- New explicit-restriction bucket now surfaces `2` rows instead of hiding them inside the open-license count.
- `Simulation and ML benchmarks` license clarity remains low at `1/4 (25%)`, but the remaining explicit row is now correctly identified as restrictive rather than open.
- `Scientific machine learning` now resolves into `1` open/permissive row and `1` explicit restrictive row among its `2` clarified-license entries.
- `FluidVerse 2D shock-induced air bubble collapse in water` no longer depends on a generic dataset-terms placeholder.

## Unresolved Risks

1. `Two-phase immersion cooler for medium-voltage silicon carbide MOSFETs` remains the highest-risk dataset row because it still depends on a Dryad sharing link and lacks an associated paper link.
2. Dataset paper-link debt remains the largest unresolved maintenance front, especially for Harvard Dataverse multimodal pool boiling, NASA DASHlink incipient boiling, the Mendeley `sound of boiling` dataset, the Dryad physical-descriptor dataset, and the Dryad transient-hysteresis dataset.
3. `Bubble_dynamics_simulation` and `Bubble_dynamics_simulation_CPP` remain the clearest repeated reduced-order bottlenecks after repeated direct rechecks, and current evidence still points to genuine upstream sparsity.
4. `MFiX`, `OpenFOAM interFoam guide`, and `OpenFOAM dispersed multiphase guide` remain the key CFD infrastructure rows with unresolved license-review or citation-treatment ambiguity.
5. GitHub API access remains blocked in this environment, so discovery automation still cannot validate live repository search results even though the archive/web search seeds remain available for manual follow-up.
6. Manuscript PDF compilation still cannot be verified in this environment because no LaTeX toolchain is installed.
