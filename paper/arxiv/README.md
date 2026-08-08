# arXiv Draft

This folder contains a draft paper describing the repository as a living catalog.

Build from this folder with:

```powershell
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

The figures in `figures/` are generated from `data/resources.csv` by:

```powershell
python ../../scripts/render_catalog.py
```

That command also regenerates the summary and reproducibility-audit markdown pages used by the repository front end.

Before submission, update the author list, affiliations, acknowledgements, and any venue-specific formatting.
