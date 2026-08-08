# Quickstart

Use this guide to choose a starting point before diving into the full catalog.

If you want the most decision-ready version, check the generated `Workflow Starter Matrix` in [summary.md](summary.md) or [reproducibility_audit.md](reproducibility_audit.md) first. If your question is specifically about reduced-order or cavitation-style bubble models, also read the new `Reduced-Order Starter Paths` table there before picking a repository.

## Pick A Workflow

| Need | Start with | Trust signal | Watch out for |
| --- | --- | --- | --- |
| Analyze pool-boiling images | [BubbleID](https://github.com/cldunlap73/BubbleID) | Domain-specific code, annotations, weights, and paired dataset | Retraining may be necessary if your optics or boiling regime differ strongly from the released data. |
| Fine-tune a general bubble image tool | [Bubble Analyser 2.0](https://github.com/dmesap/bubble_analyser) or [scikit-image](https://scikit-image.org/) | Mature reusable image-analysis tooling | Flexible utility does not mean bubble-specific validation. |
| Segment high-speed video across fluid conditions | [VideoSAM](https://github.com/chikap421/videosam) | Open video-segmentation code, data, and paper | Inspect edge cases such as glare, overlap, and rare phase morphology. |
| Predict heat flux from hydrophone, AE, or image sequences | [SeqReg](https://github.com/cldunlap73/SeqReg) | Strongest current signal-regression stack with paired benchmark-ready datasets | Avoid leakage by splitting by experiment or surface. |
| Benchmark neural PDE or operator-learning models | [Bubbleformer](https://github.com/HPCForge/Bubbleformer) with [BubbleML 2.0](https://huggingface.co/datasets/hpcforge/BubbleML_2) | Direct paper link plus benchmark-oriented simulation dataset | Forecast accuracy on simulations does not guarantee experimental transfer. |
| Explore fast surrogates for two-phase cooling | [NUCLEUS](https://github.com/therml-ai/NUCLEUS) with [BubbleML](https://github.com/HPCForge/BubbleML) | Rich surrogate stack and current BubbleML-family support | NUCLEUS is reuse-restricted, and BubbleML still needs manual GitHub license confirmation. |
| Run interface-resolved multiphase CFD | [Basilisk](https://basilisk.fr/), [Aphros](https://github.com/cselab/aphros), or [OpenFOAM](https://www.openfoam.org/) | Strong solver lineage plus verification-oriented examples | Mesh, contact angle, phase-change model, and validation still dominate trust. |
| Run compressible bubble or cavitation CFD | [MFC](https://github.com/MFlowCode/MFC) | Direct software citation and compressible multiphase focus | Use it when shocks or compressibility matter, not as a default for all boiling cases. |
| Build a simple single-bubble model | the [Basilisk Rayleigh-Plesset test](https://basilisk.fr/src/test/bubble.h) first, then [Bubble-dynamic](https://github.com/BerryWei/Bubble-dynamic) | Reference-backed anchor plus a paper-backed pedagogical companion | Treat prototype-style reduced-order repos as educational until equations, parameters, and reuse terms are independently checked. |
| Study cavitation-bubble acoustics | [APECSS](https://github.com/polycfd/apecss) | Explicit open license plus a software paper and example-driven cavitation workflow | Good for spherical pressure-driven cavitation bubbles, not for boiling-specific wall heat-transfer closures. |

## Choose A Dataset First

If your workflow starts with data rather than code, check the dataset adoption ladder in [summary.md](summary.md) or [reproducibility_audit.md](reproducibility_audit.md) before downloading in bulk.

- Prefer `Benchmark-ready` rows when you need a defendable baseline or a dataset you may cite directly in a manuscript.
- Treat `Citation-verified dataset` rows as useful but still citation-chasing work, especially when the archive proves the title but not a stable article URL.
- Treat `Archive-only discovery lead` and `Access-risky transfer dataset` rows as exploratory sources until you verify provenance, access stability, and fit to your regime.

## Minimum Reproducibility Checklist

Before trusting a tool for a new experiment or simulation regime, record:

- Geometry, working fluid, pressure, temperature, heat flux or wall superheat, and surface condition.
- Data modality and acquisition settings: frame rate, exposure, field of view, sampling rate, sensor location, and synchronization.
- Model or solver assumptions: segmentation classes, tracking criteria, CFD phase-change model, contact angle, mesh, train/test split, and extrapolation limits.
- Output units and definitions: bubble diameter convention, vapor area fraction, departure event definition, heat-flux label timing, and uncertainty.
- A visual sanity check: raw input, processed mask or field, extracted metric, and one failure case.

## Evidence Before Convenience

Before defaulting to the newest or flashiest entry, check [`reproducibility_audit.md`](reproducibility_audit.md).

- Prefer entries with code or data plus an associated paper when you need a benchmark or a method you can defend in a manuscript.
- Treat generic license labels such as `Repository license` or `NOASSERTION` as a prompt to inspect the upstream project before redistributing or embedding the tool in your own pipeline.
- In reduced-order work, distinguish `Reference-backed`, `Paper-backed, license unclear`, and `Code-backed, paper sparse` rows in [`reproducibility_audit.md`](reproducibility_audit.md), and use the new reduced-order starter-path matrix there before you adopt a solver or benchmark as scientific ground truth.
- If your regime is compressible, cavitating, or shock driven, do not assume a boiling-oriented incompressible VOF tool is the right starting point.

## Typical First Runs

### BubbleID-Style Image Analysis

1. Convert raw videos into frames in the format expected by the package.
2. Run a small representative case with the released weights.
3. Inspect masks, attached/detached labels, and tracks before batch processing.
4. Fine-tune or relabel if your heater, illumination, pressure, or fluid differs strongly from the training data.

### SeqReg-Style Signal Regression

1. Align the hydrophone, AE, image-derived, and heat-flux labels in time.
2. Split by experiment or surface, not by random windows from the same run.
3. Compare a simple spectral or statistical baseline with the sequence model.
4. Plot prediction error versus heat flux, regime, and transient direction.

### SciML Forecasting With BubbleML

1. Start with a small streamed subset before downloading large HDF5 files.
2. Verify variable names, units, and boundary-condition metadata.
3. Reproduce a baseline notebook or checkpoint before changing architecture.
4. Evaluate physical metrics such as interface geometry, heat-flux consistency, and mass conservation, not only pixel error.

## Where To Go Next

- Full catalog: [catalog.md](catalog.md)
- Summary figures and trend notes: [summary.md](summary.md)
- Evidence and license audit: [reproducibility_audit.md](reproducibility_audit.md)
- Curation/update process: [curation_workflow.md](curation_workflow.md)
