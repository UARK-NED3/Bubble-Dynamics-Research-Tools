# 2026-06-23 Review, Revision, and Verification

## Independent Reviewer Comments

1. The main critique from the previous three runs still held at the start of this pass: the audit was bottlenecked less by obviously weak projects than by a small cluster of high-impact CFD and utility entries whose citations or licenses had never been transferred into the CSV.
2. The prior revision materially improved utility and baseline-solver coverage, but it still left too much of the CFD category looking under-documented. Aphros, JumpingBubbles, the viscoelastic Worthington-jet repo, Outflow-Forcing-BubbleML, and FluidX3D were still dragging the paper-link audit even though upstream pages exposed enough evidence to curate them more precisely.
3. License handling had become a scientific-usability issue, not only a legal metadata issue. The catalog was still implicitly treating some entries as open just because source code was visible, which risks misleading downstream users about reuse constraints.
4. General image and flow utilities had one recurring weak spot left: PIVlab is a standard tool in lab workflows, so leaving its license and canonical citation unresolved made the utility category look less mature than it really is.
5. The reduced-order category remains the most fragile part of the catalog. The two Kozak repos still lack explicit licensing and associated paper links, and that repeated gap now stands out more sharply because other categories improved.
6. Manuscript and README framing needed one more step: they had to explain that curation quality includes correcting over-optimistic license assumptions, not only backfilling missing papers.

## Repetition Compared With 2026-06-22

- Repeated from prior day: yes.
- Recurring issue: metadata debt remained concentrated in a short list of named CFD, reduced-order, and utility entries.
- Assessment: the June 22 revision fixed many foundational citations, but it still left too many directly verifiable solver/software entries unresolved, so a targeted source-verification pass was necessary.

## Substantive Author-Maintainer Revisions

1. Backfilled verified citation and license metadata in [`data/resources.csv`](../data/resources.csv) for recurring audit bottlenecks:
   - `PIVlab` -> `MIT` license via the official GitHub repo and JORS citation `10.5334/jors.334`
   - `JumpingBubbles` -> `GPL-3.0` plus Zenodo software citation `10.5281/zenodo.14602623`
   - `Viscoelastic Worthington jets and droplets produced by bursting bubbles` -> `GPL-3.0` plus JFM paper `10.1017/jfm.2025.237`
   - `Aphros` -> linked to upstream method/citation anchor `10.1126/sciadv.abm0590`
   - `Outflow-Forcing-BubbleML` -> marked `archived` and linked to the outflow-forcing paper `arXiv:2306.10174`
   - `FluidX3D` -> corrected from an overstated open-license label to explicit `Source-available non-commercial terms`, with its upstream thesis citation `10.15495/EPub_UBT_00005400`
2. Updated [`scripts/render_catalog.py`](../../scripts/render_catalog.py) so the generated audit distinguishes `Source-available non-commercial` entries from true open licenses and explains the reuse implications directly in the audit guidance.
3. Revised [`README.md`](../../README.md) to reflect the corrected CFD/software evidence, the archived status of Outflow-Forcing-BubbleML, and the new distinction between open and non-commercial source-available resources.
4. Revised [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) and [`paper/arxiv/references.bib`](../../paper/arxiv/references.bib) to document the stronger curation pass, add a PIVlab citation, and make the license-classification nuance explicit in the manuscript argument.
5. Regenerated [`docs/catalog.md`](../catalog.md), [`docs/summary.md`](../summary.md), [`docs/reproducibility_audit.md`](../reproducibility_audit.md), and the figures under [`figures`](../../figures) and [`paper/arxiv/figures`](../../paper/arxiv/figures).

## Verification Run

- `python scripts/render_catalog.py --validate-only`
- `python scripts/render_catalog.py`
- Inspected regenerated `docs/summary.md`, `docs/reproducibility_audit.md`, and README/manuscript deltas for consistency with the direct source-verification findings

## Measured Outcome After This Run

- `Partial link coverage` decreased from `27` to `21`.
- `Code + paper/docs` increased from `11` to `17`.
- `Explicit open license` increased from `23` to `25`, while `Source-available non-commercial` is now tracked explicitly as `1` instead of being conflated with open licensing.
- `Manual license review` decreased from `15` to `12`.
- `CFD and multiphase simulation` paper-link coverage increased from `18%` to `64%`.
- `CFD and multiphase simulation` license clarity increased from `55%` to `73%`.
- `CFD and multiphase simulation` strong evidence bundles increased from `4` to `9`.
- `General image and flow utilities` paper-link coverage increased from `57%` to `71%`.
- `General image and flow utilities` license clarity increased from `86%` to `100%`.

## Unresolved Risks

1. `Bubble_dynamics_simulation` and `Bubble_dynamics_simulation_CPP` still dominate reduced-order metadata debt because they expose neither explicit licenses nor associated paper links.
2. `OpenFOAM` and `MFiX` remain the most important unresolved CFD infrastructure entries in the manual-review queue.
3. `BubbleML` still lacks an explicit upstream license file in the catalog despite being a key benchmark.
4. Several datasets still lack paper links, especially the Harvard Dataverse multimodal boiling dataset, NASA DASHlink incipient boiling data, and the remaining Dryad/Mendeley mirrors.
5. Manuscript PDF compilation still cannot be verified in this environment because no LaTeX toolchain is installed.
