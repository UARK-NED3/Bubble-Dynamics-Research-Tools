# 2026-07-05 Review, Revision, and Verification

## Independent Reviewer Comments

1. The July 4 reduced-order triage revision materially improved the weakest code category, but it exposed the next user-facing weakness more clearly: data-bearing resources were still described through audit counts rather than an explicit trust-order ladder for researchers deciding what to download, benchmark, or cite first.
2. That gap mattered across multiple categories, not only the `Datasets` bucket. The current repo mixes benchmark-grade archives such as BubbleID-style and BubbleML-style resources with citation-verified but URL-unresolved Dryad rows, archive-only discovery leads such as NASA DASHlink and the Harvard Dataverse multimodal row, and transfer-only or access-risky data rows such as the immersion-cooling sharing link and FluidNexus datasets. Users still had to infer that hierarchy manually.
3. A second maintainability issue remained in a smaller but still important form: several source notes that feed the audit logic were scientifically correct but not specific enough to help users understand why a row remained reusable, exploratory, or risky. The BURST row and the kozakaron C++ sonochemistry row were the clearest examples because both public pages expose more workflow detail than the prior notes conveyed.
4. The manuscript and quickstart narrative also lagged the generated outputs. They now discussed reduced-order trust ordering, but not yet the same trust-order logic for dataset selection, which created an avoidable mismatch between the repo's strongest generated guidance and its human-facing entry points.

## Repetition Compared With 2026-07-04

- Repeated from prior day: yes, at the level of critique pattern.
- Recurring issues:
  - the repo still needed adoption-ladder guidance instead of asking users to synthesize trust from debt tables;
  - the reduced-order version of that critique was largely fixed on July 4, but the same usability failure had shifted to the dataset layer;
  - source-note specificity still mattered because the audit and priority logic depend on those row-level descriptions.
- Assessment: the July 4 pass was not insufficient on reduced-order work itself. It was successful enough to reveal the next structurally similar gap, so today required another renderer-level usability revision rather than a wording-only cleanup.

## Substantive Author-Maintainer Revisions

1. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) with a dataset-readiness model for all data-bearing resources (`Dataset` and `Code and dataset` rows). The generated summary and reproducibility audit now include a `Dataset Adoption Ladder` that classifies rows as `Benchmark-ready`, `Citation-verified dataset`, `Archive-only discovery lead`, or `Access-risky transfer dataset`.
2. Regenerated [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) so the dataset ladder is rendered as a first-class decision aid instead of leaving users to combine evidence tables, blocker tables, and row notes on their own.
3. Refreshed source-verified catalog rows in [`data/resources.csv`](../../data/resources.csv) for:
   - `BURST`, whose public GitHub README now records a dual-camera YOLO workflow for bubble size distribution, rise velocity, and volumetric flow-rate estimation;
   - `Bubble_dynamics_simulation_CPP`, whose public GitHub page now records packaged releases, JSON-driven command-line runs, Python/MATLAB interfaces, and a SUNDIALS CVODE core while still lacking explicit licensing and paper metadata.
4. Revised [`README.md`](../../README.md), [`docs/quickstart.md`](../quickstart.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the human-facing narrative now explains the July 5 dataset adoption ladder and points users to the new `start here first` guidance.
5. Regenerated [`docs/discovery_candidates.md`](../discovery_candidates.md) during validation so the discovery artifact remains in sync with the current source table and gap priorities.

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- `python scripts/discover_candidates.py --output docs/discovery_candidates.md`
- Checked regenerated [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), [`docs/quickstart.md`](../quickstart.md), [`README.md`](../../README.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) for:
  - the new `Dataset Adoption Ladder` section and readiness counts;
  - `Benchmark-ready` rows surfacing expected core anchors such as BubbleID-style, VideoSAM, and BubbleML/BubbleML 2.0 resources;
  - citation-verified Dryad rows staying separate from archive-only discovery leads;
  - refreshed BURST and kozakaron C++ notes propagating into the generated catalog;
  - manuscript date and narrative updates reflecting the July 5 pass.
- Manuscript PDF compilation still could not be verified here because no LaTeX toolchain is installed in the environment.

## Measured Outcome After This Run

- The next repeated usability critique is now addressed structurally rather than rhetorically: users can choose data sources by readiness class instead of reading several audit tables and inferring trust order themselves.
- The repo now exposes matching adoption ladders for both of the most comment-prone layers: reduced-order code and data-bearing resources.
- Row-level source notes for BURST and the kozakaron C++ solver are more specific, which improves both user interpretation and the stability of future audit classifications.

## Unresolved Risks

1. The two kozakaron reduced-order repositories still lack explicit public license files and associated paper links, so they remain technically interesting but reuse-risky.
2. Several core datasets still have genuinely unresolved public paper discoverability or absent paper evidence, especially the NASA DASHlink incipient-boiling row, the Harvard Dataverse multimodal row, and the Mendeley `sound of boiling` row.
3. The immersion-cooling sharing-link dataset remains an access-stability risk, and FluidNexus datasets remain transfer-oriented rather than direct bubble/boiling anchors even though both are now placed more honestly in the dataset ladder.
4. BubbleML remains benchmark-useful but still carries manual license-review debt because the public repository page did not surface a standalone license file during direct verification.
5. Manuscript PDF compilation still cannot be validated in this environment because no LaTeX toolchain is installed.
