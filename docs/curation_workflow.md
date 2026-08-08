# Curation Workflow

This repository is a living catalog. Additions should make the repository easier to use for bubble-dynamics researchers, not just longer.

## Source Of Truth

- Edit [`data/resources.csv`](../data/resources.csv) for catalog entries.
- Run `python scripts/render_catalog.py` after editing the CSV.
- Review generated changes in [`docs/catalog.md`](catalog.md), [`docs/summary.md`](summary.md), [`docs/reproducibility_audit.md`](reproducibility_audit.md), and `figures/`.
- Check whether the generated `Workflow Starter Matrix` and `Reduced-Order Starter Paths` tables in [`docs/summary.md`](summary.md) and [`docs/reproducibility_audit.md`](reproducibility_audit.md) still give sensible first-stop recommendations after your edits.
- Do not edit generated catalog or summary files by hand.

## Acceptance Criteria

Include a resource when it satisfies at least one condition:

- It provides open code, data, model weights, examples, or documentation that can support a reproducible bubble-dynamics workflow.
- It targets boiling vapor bubbles, gas-liquid bubbles, cavitation/sonochemistry bubbles, bubble columns, foams, or interface-resolved multiphase simulation.
- It is an adjacent utility that is practically useful for images, acoustic signals, thermal data, CFD fields, tracking, annotations, or reduced-order bubble models.
- It is a name-collision entry that prevents users from confusing a similarly named non-fluid project with a bubble-dynamics tool.

Avoid adding a resource when:

- It is only a paper with no reusable artifact, unless it defines a key dataset, benchmark, or method needed to understand the catalog.
- It has no clear link to bubble dynamics, boiling, multiphase flow, phase-change diagnostics, or reusable analysis infrastructure.
- The link is unstable, private, inaccessible, or cannot be checked.

## Recurring Search Routine

Monthly or before a release:

1. Run `python scripts/discover_candidates.py --output docs/discovery_candidates.md`.
2. If the environment blocks live GitHub API access, use the generated `Gap-Targeted Priorities` section first; it is built from the current catalog and keeps the discovery pass useful offline.
3. Review the generated `Manual Web Search Seeds` and `Manual Archive Search Seeds` sections so discovery is not limited to GitHub repositories.
4. Check GitHub topics such as `boiling`, `two-phase`, `bubble-dynamics`, `computer-vision`, `neural-operator`, and `multiphase-flow`.
5. Check data archives: Dryad, Mendeley Data, Harvard Dataverse, Hugging Face, NASA DASHlink, Zenodo, and institutional repositories.
6. For every candidate, inspect the README, license, examples, dependencies, data format, and associated publication.
7. Add only screened resources to `data/resources.csv`, then regenerate the catalog and figures.

## Metadata Rules

- `year`: use the resource publication year, dataset publication year, first paper year, or first public release year. Prefer the year that best explains the trend figure.
- `status`: use `active`, `archived`, `deprecated`, `review sharing`, or `adjacent`.
- `license`: use the SPDX identifier when obvious; otherwise use `Repository license`, `Dataset terms`, `Archive terms`, `Documentation terms`, or `NOASSERTION`.
- Treat `CC BY`, `CC BY-SA`, and `CC0` as open/permissive sharing terms, but treat `CC BY-NC`, `CC BY-ND`, and `CC BY-NC-ND` as explicitly restrictive rather than open-source equivalents.
- `source_checked`: update to the date when the entry was last manually inspected.
- `notes`: explain what a user can actually do with the resource. Avoid hype.

The generated reproducibility audit uses these fields to surface manual-review priorities. Generic values such as `Repository license` and `NOASSERTION` are acceptable placeholders during curation, but they should trigger later cleanup rather than becoming invisible debt. The audit now also distinguishes whether unresolved debt looks like `catalog backfill`, `citation discoverability`, `upstream sparsity`, or `access/link stability`, separates `open/permissive` from `explicit restrictive` reuse terms so the catalog does not overstate downstream reuse rights, and filters a dedicated `Backfill-Ready Queue` for rows where repeated comments should trigger direct metadata transfer instead of another upstream spot-check. If a direct check shows that the public page still lacks a visible license file, repository-level license badge, stable paper link, software citation, or public thesis URL, encode that explicitly in `notes` so the row graduates from false `catalog backfill` into documented `upstream sparsity`. If the public page proves the paper title or project citation trail but still does not surface a canonical article URL or DOI, say that explicitly in `notes`; the audit will treat the row as `citation discoverability` rather than as fully missing paper evidence. Documentation pages should be handled separately from standalone code artifacts: if the page is valuable because it belongs to a clearly licensed parent project, say that directly instead of treating the documentation page as if it must ship its own standalone SPDX artifact.
The audit also assigns each entry a scope-alignment bucket: `core bubble/boiling`, `adjacent but directly useful`, or `peripheral or transfer-only`. Use that label when recurring review comments complain about scientific focus or curation scope. A peripheral transfer-only row can stay in the catalog when it is genuinely useful, but it should not outrank core bubble-dynamics debt in the maintenance frontier just because it has an old unchecked sharing link. For reduced-order rows, read the generated `Reduced-Order Starter Paths` matrix first, then the `Reduced-Order Snapshot` or `Reduced-Order Triage` tables; the point is to separate pedagogical baselines, sonochemistry-oriented repositories, and cavitation-acoustics tooling before you label the entire category as one weakness.

## Validation

Run:

```powershell
python scripts/render_catalog.py --validate-only
python scripts/render_catalog.py
git diff -- README.md docs data figures paper/arxiv
```

When recurring review comments appear on consecutive daily passes, start with the generated `Backfill-Ready Queue` in [`docs/reproducibility_audit.md`](reproducibility_audit.md). If the row still sits in `catalog backfill`, the next revision should change the CSV notes, links, or classification logic. If a fresh source check instead confirms that the public page still does not expose the missing license or paper evidence, or the only landing page is gated behind JavaScript verification and repeated title/DOI searches do not surface a stable citation, move the row to documented `upstream sparsity` rather than rechecking it again the next day. If the page exposes a verified title or citation trail but no stable article URL, move the row to `citation discoverability` and stop treating it as easy maintainer backfill. If it remains `upstream sparsity`, `citation discoverability`, or `access/link stability`, document that explicitly and move to a different row instead of repeating the same shallow verification. Before spending time on any row above the fold of the frontier, confirm its `Scope alignment` column so repeated work is spent on the most direct bubble-dynamics weaknesses first.

For code or model entries, do not imply validation in a new physical regime unless the source documents mesh independence, sensor calibration, train/test split discipline, uncertainty, or experimental comparison.

## Candidate Triage Questions

- What physical regime does the tool actually cover?
- What input does it require and what output does it produce?
- Does it provide runnable examples, data, weights, or environment instructions?
- What license or archive terms apply?
- Does it generalize, or is it tightly coupled to one apparatus, fluid, surface, or simulation setup?
- What failure modes should a user inspect before trusting the output?
- Does the entry expose enough evidence to earn a strong bundle in the audit: code, data, paper, license clarity, and runnable examples?
