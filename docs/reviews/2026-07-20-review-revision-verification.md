# 2026-07-20 Review, Revision, and Verification

## Independent Reviewer Comments

1. The July 6 workflow matrix fixed the broad `what should I try first` problem, but a narrower version of the same critique remained in the reduced-order layer. Users still saw reduced-order mostly as a debt category rather than as a set of distinct use cases with different trust levels and different best-entry tools.
2. That recurrence mattered because reduced-order resources are not interchangeable. A pedagogical Rayleigh-Plesset baseline, a sonochemistry-focused single-bubble simulator, and a cavitation-acoustics package should not all sit under one generic warning label when their evidence and intended use differ materially.
3. A second reviewer concern was that some of the most visible remaining `no paper evidence` debt was becoming stale or misleading. The Harvard multimodal boiling dataset and the kozakaron sonochemistry repositories were important enough that another shallow pass would have been inadequate if stable public article links now existed.
4. The discovery workflow also still leaned too heavily toward general reduced-order search phrases. If the repository now treats cavitation acoustics as a distinct reduced-order lane, the search seeds should reflect that explicitly.

## Repetition Compared With 2026-07-06

- Repeated from prior day: yes, at the pattern level.
- Recurring issues:
  - the repository still needed a stronger `start here first` layer inside reduced-order work rather than only a backlog-oriented triage table;
  - repeated reduced-order critique was no longer mainly about missing rows, but about missing separation between pedagogical baselines, sonochemistry repositories, and cavitation-acoustics tooling;
  - several headline debt rows needed a deeper source-verification pass instead of another generic `no paper evidence` note.
- Assessment: the July 6 revision was useful but not sufficient for reduced-order users. It solved workflow-level first-use guidance across the whole repo, but it did not yet disambiguate the reduced-order layer itself.

## Substantive Author-Maintainer Revisions

1. Added a new reduced-order entry in [`data/resources.csv`](../data/resources.csv): `APECSS`, an explicitly licensed cavitation-bubble dynamics package with a public software-paper DOI and release-backed examples.
2. Upgraded direct paper evidence for three previously weak rows in [`data/resources.csv`](../data/resources.csv):
   - the Harvard Dataverse multimodal boiling dataset now points to its paired Data in Brief article;
   - `Bubble_dynamics_simulation` now points to the official OGET article that explicitly cites the Python repository as the code release;
   - `Bubble_dynamics_simulation_CPP` now points to the 2026 Ultrasonics Sonochemistry article that explicitly cites the C++ repository.
3. Extended [`scripts/render_catalog.py`](../../scripts/render_catalog.py) with a generated `Reduced-Order Starter Paths` matrix and improved reduced-order ordering so the category now distinguishes:
   - pedagogical Rayleigh-Plesset baselines;
   - sonochemistry-focused reduced-order repositories;
   - cavitation-acoustics tooling.
4. Updated human-facing docs and manuscript narrative in [`README.md`](../../README.md), [`docs/quickstart.md`](../quickstart.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) so the July 20 pass is reflected outside the CSV and renderer logic.
5. Refreshed generated markdown outputs directly in [`docs/catalog.md`](../catalog.md), [`docs/summary.md`](../summary.md), and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) to keep the catalog, adoption ladders, reduced-order guidance, and maintenance frontier synchronized with the revised source data despite the local Python-runtime blocker.
6. Expanded reduced-order discovery coverage in [`data/discovery_queries.json`](../../data/discovery_queries.json) with an explicit cavitation-acoustics query plus matching web and archive search seeds.

## Verification Run

- Attempted:
  - `python scripts/render_catalog.py --validate-only`
  - `python scripts/render_catalog.py`
  - `python scripts/discover_candidates.py --output docs/discovery_candidates.md`
  - `py -3 scripts/render_catalog.py --validate-only`
  - `py -3 scripts/render_catalog.py`
  - `py -3 scripts/discover_candidates.py --output docs/discovery_candidates.md`
- Result:
  - validation and regeneration were blocked by the local Python environment;
  - `python` is not on PATH in this shell;
  - `py` resolves to a Windows Store Python stub that fails to launch and direct execution of the underlying `python3.13.exe` is denied in this environment.
- Manual verification completed instead:
  - checked [`data/resources.csv`](../../data/resources.csv) for the new APECSS row plus upgraded paper links and notes;
  - checked [`docs/catalog.md`](../catalog.md) for the new reduced-order entry and refreshed Harvard/kozak row notes;
  - checked [`docs/summary.md`](../summary.md) and [`docs/reproducibility_audit.md`](../reproducibility_audit.md) for updated counts, the reduced-order starter-path matrix, revised reduced-order readiness states, and the recalculated maintenance frontier;
  - checked [`README.md`](../../README.md), [`docs/quickstart.md`](../quickstart.md), [`docs/curation_workflow.md`](../curation_workflow.md), and [`paper/arxiv/main.tex`](../../paper/arxiv/main.tex) for consistent July 20 narrative updates.

## Measured Outcome After This Run

- Reduced-order guidance is now split into three task-specific lanes instead of one mostly negative category: pedagogical baseline, sonochemistry model, and cavitation-acoustics model.
- The Harvard multimodal boiling dataset moved from `archive-only discovery lead` style debt into a `Benchmark-ready` direct-paper row.
- Both kozakaron sonochemistry repositories moved out of the top `no paper evidence` backlog and now read as paper-backed but still license-unclear.
- The reduced-order maintenance frontier no longer overstates the kozakaron rows as paperless; remaining top debt is now concentrated more honestly in NASA DASHlink, the immersion-cooling sharing link, `bubble-dynamics-resnet`, the Mendeley `sound of boiling` dataset, and sparse optical/SciML rows.

## Unresolved Risks

1. The local Python environment is broken in this workspace, so figures were not regenerated and `docs/discovery_candidates.md` was not rerendered from the updated discovery-query file during this run.
2. The kozakaron sonochemistry repositories still do not expose explicit license files on their public repository pages, so downstream redistribution and derivative-use terms remain unclear.
3. `BubbleML` and the two Zhou repositories still carry license-review debt despite stronger technical notes and workflow positioning.
4. Several high-priority dataset rows still lack stable public paper evidence, especially NASA DASHlink, the immersion-cooling review-sharing dataset, the Mendeley `sound of boiling` dataset, and the FluidVerse shock-bubble dataset.
5. Manuscript PDF compilation still could not be verified here because no working LaTeX toolchain is installed, and the broken Python environment also prevented a clean rerender/validate pass for figures and generated markdown.
