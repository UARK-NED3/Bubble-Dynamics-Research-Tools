# Awesome Bubble Dynamics Research Tools

> A curated library of datasets, code, and analysis tools for bubble dynamics research: vapor bubbles during boiling, gas bubbles in liquids, optical imaging, acoustic emissions, thermal imaging, and CFD/SciML simulations.

Inspired by the structure of [Awesome Auto Research Tools](https://github.com/handsome-rich/Awesome-Auto-Research-Tools), this list favors practical research artifacts: open datasets, runnable code, documented workflows, and packages that can support reproducible studies.

Last checked: 2026-05-21.

## Contents

- [Scope](#scope)
- [Quick Picks](#quick-picks)
- [Datasets](#datasets)
- [Optical Imaging and Computer Vision](#optical-imaging-and-computer-vision)
- [Acoustics and Acoustic Emissions](#acoustics-and-acoustic-emissions)
- [Thermal and Infrared Imaging](#thermal-and-infrared-imaging)
- [Reduced-Order Bubble Dynamics](#reduced-order-bubble-dynamics)
- [CFD and Multiphase Simulation](#cfd-and-multiphase-simulation)
- [Scientific Machine Learning](#scientific-machine-learning)
- [General Image and Flow Analysis Utilities](#general-image-and-flow-analysis-utilities)
- [Adjacent or Name-Collision Projects](#adjacent-or-name-collision-projects)
- [Contributing](#contributing)

## Scope

Included resources should be useful for at least one of these workflows:

- Extract bubble shape, centroid, diameter, departure, coalescence, interface velocity, or vapor fraction from images or videos.
- Analyze boiling acoustics, hydrophone data, or hit-based acoustic emission data.
- Estimate heat flux, boiling regime, CHF proximity, or thermal state from optical, acoustic, or thermal measurements.
- Simulate vapor bubbles, gas bubbles, bubbly flows, foams, cavitation-like oscillations, or interface-resolved multiphase flows.
- Train or benchmark ML/SciML models on bubble or boiling dynamics.

## Quick Picks

| Need | Start with | Why |
| --- | --- | --- |
| Labeled pool-boiling bubble images and pretrained models | [BubbleID dataset](https://datadryad.org/dataset/doi:10.5061/dryad.ksn02v7gx) + [BubbleID code](https://github.com/cldunlap73/BubbleID) | Raw and annotated boiling images, model checkpoints, segmentation, classification, tracking, and interface statistics. |
| Multimodal boiling measurements | [Harvard Dataverse pool boiling dataset](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/6GLGC6) | Synchronized thermal, acoustic, AE, and high-speed image data for steady and transient pool boiling. |
| Acoustic heat-flux regression | [SeqReg](https://github.com/cldunlap73/SeqReg) | Sequence-regression package for hydrophone, AE, and image-based boiling heat-flux prediction. |
| Simulation benchmark for ML on boiling | [BubbleML](https://github.com/HPCForge/BubbleML) and [BubbleML 2.0](https://huggingface.co/datasets/hpcforge/BubbleML_2) | Simulation-derived multiphase fields for optical flow, operator learning, and long-horizon forecasting. |
| Interface-resolved bubble CFD | [Basilisk](https://basilisk.fr/), [Aphros](https://github.com/cselab/aphros), [OpenFOAM](https://www.openfoam.org/) | Mature open-source multiphase solvers with VOF/interface-capturing examples. |

## Datasets

### Boiling, Multimodal, and Heat-Flux Datasets

| Resource | Modality | Best for | Notes |
| --- | --- | --- | --- |
| [Pool Boiling Dataset: Synchronized Acoustic, Optical, and Thermal Measurements](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/6GLGC6) | Optical, hydrophone, AE, thermocouple-derived heat flux | Multimodal boiling, CHF, regime monitoring | Harvard Dataverse dataset associated with a Data in Brief article; includes steady-state and transient tests on polished copper, microchannels, and copper foams. |
| [BubbleID: A deep learning framework for bubble interface dynamics analysis](https://datadryad.org/dataset/doi:10.5061/dryad.ksn02v7gx) | High-speed optical images, annotations, model weights | Bubble segmentation, attached/detached classification, tracking, interface dynamics | Dryad dataset with raw/annotated images, pretrained segmentation and classification checkpoints, and tutorials. |
| [Unveiling hysteresis of transient boiling: A multimodal perspective](https://datadryad.org/dataset/doi:10.5061/dryad.ksn02v7h2) | Optical video, hydrophone, microphone, AE, temperature | Boiling hysteresis, CHF-cycle behavior, multimodal diagnostics | Transient pool boiling on copper foam and flat copper surfaces; includes raw `.cine`, `.lvm`, `.DTA`, `.txt`, and MP4 access copies. |
| [Nonintrusive heat flux quantification using acoustic emissions during pool boiling](https://datadryad.org/dataset/doi:10.5061/dryad.q573n5tvq) | Hydrophone, temperature, bubble images | Acoustic heat-flux regression and synchronized image context | Dataset used with SeqReg/HydReg-style workflows; includes sound-heat-flux CSV and high-speed image folder. |
| [Hit2Flux: boiling heat flux prediction using hit-based AE sensing](https://datadryad.org/dataset/doi:10.5061/dryad.g79cnp628) | AE hits/waveforms, hydrophone, pressure, temperature | Hit-based acoustic emission modeling, sequence-of-sequences LSTM inputs | Includes `.DTA`, AE hit text files, per-hit waveform CSVs, hydrophone files, pressure files, and thermal measurements. |
| [A temporal-spatial framework for efficient heat flux monitoring of transient boiling](https://datadryad.org/dataset/doi:10.5061/dryad.6m905qgc7) | Boiling videos, hydrophone, temperature | Image-sequence heat-flux monitoring | Eleven transient boiling tests with MP4 videos converted from Phantom `.cine` files plus synchronized thermal/acoustic files. |
| [Two-phase immersion cooler for medium-voltage silicon carbide MOSFETs](https://datadryad.org/share/_SEP3K4u6OjIrECuTetxr2AqVoqs5EKJOl8yusAWL8c) | IR video, thermocouples, CSV temperature histories | Two-phase immersion cooling and IR-based hotspot histories | Peer-review sharing link at time of check; useful for thermal/IR workflows, less directly bubble-interface focused. |
| [Deep learning the sound of boiling for advance prediction of boiling crisis](https://data.mendeley.com/datasets/vnnzc7n97m/1) | Audio, MATLAB code | Boiling regime classification and CHF advance prediction from sound | Mendeley Data dataset with raw audio files and MATLAB classification scripts. |
| [Generalizable physical descriptors of pool boiling heat transfer from unsupervised learning of images](https://datadryad.org/dataset/doi:10.5061/dryad.kh18932mw) | High-speed images, contours, MATLAB analysis | Physical descriptors from boiling images | Includes image datasets and contour/descriptor data for bubble size, count, vapor area fraction, and PCA descriptors. |

### Simulation and ML Benchmark Datasets

| Resource | Modality | Best for | Notes |
| --- | --- | --- | --- |
| [BubbleML](https://github.com/HPCForge/BubbleML) | CFD-derived multiphase fields | SciML, optical flow, operator learning | NeurIPS 2023 Spotlight dataset and benchmarks for nucleate pool boiling, flow boiling, and subcooled boiling. |
| [BubbleML 2.0](https://huggingface.co/datasets/hpcforge/BubbleML_2) | HDF5 time-series fields, metadata, train/test splits | Long-horizon boiling forecasting | Includes single-bubble, saturated pool boiling, subcooled pool boiling, and flow-boiling subsets across FC-72, liquid nitrogen, and R515B. |
| [FluidNexus datasets](https://huggingface.co/datasets/yuegao/FluidNexusDatasets) | Multi-view videos and processed frames | 3D fluid reconstruction from video | Not bubble-specific, but relevant for reconstructing and predicting fluid motion from limited visual observations. |
| [FluidVerse 2D shock-induced air bubble collapse in water](https://huggingface.co/datasets/FluidVerse/2D_SABW_SSOO) | CFD fields | Shock-bubble interaction and compressible multiphase benchmarks | Useful for gas-bubble collapse regimes outside boiling. |

## Optical Imaging and Computer Vision

| Tool | Stack | Best for | Notes |
| --- | --- | --- | --- |
| [BubbleID](https://github.com/cldunlap73/BubbleID) | Python, PyTorch, Detectron2, OCSORT | Pool-boiling bubble segmentation, classification, tracking, interface metrics | Trained on manually labeled boiling data; outputs departure classification, velocity/interface predictions, and bubble statistics. |
| [BubMask](https://github.com/ywflow/BubMask) | Python, TensorFlow 1.x, Keras, Mask R-CNN | Bubble mask extraction from experimental multiphase-flow images | Outputs colored masks, per-bubble logical masks, and properties such as centroid, area, axes, and orientation. |
| [SeqReg ImgReg workflow](https://github.com/cldunlap73/SeqReg) | Python, TensorFlow, scikit-learn | Image-sequence regression from boiling images | Provides ImgReg-style pretrained workflow for heat-flux prediction from optical image sequences. |
| [BubbleNet](https://github.com/hanfengzhai/BubbleNet) | Python, TensorFlow, MATLAB/Octave plotting | Physics-informed prediction of micro-bubble dynamics | Semi-physics-informed neural network for inferring bubble flow in microfluidics. |
| [FluidNexus](https://github.com/ueoo/FluidNexus) | PyTorch, 3D Gaussian splatting, video generative models | 3D fluid reconstruction and future prediction from a single video | General fluid method rather than a bubble-specific package; relevant for visual reconstruction pipelines. |
| [BURST](https://github.com/BUbbleRST/BURST/) | Python | Bubble detection/tracking for gas bubbles in natural/experimental image sequences | Developed for bubble rise, ascent, and bursting workflows; useful when boiling-specific models do not transfer. |

## Acoustics and Acoustic Emissions

| Tool or Dataset | Signal Type | Best for | Notes |
| --- | --- | --- | --- |
| [SeqReg](https://github.com/cldunlap73/SeqReg) | Hydrophone, AE, image sequences | Regression from sequential experimental signals | Includes HydReg, Hit2Flux, and ImgReg model workflows; supports FFT preprocessing and experiment-wise CSV data organization. |
| [Hit2Flux dataset](https://datadryad.org/dataset/doi:10.5061/dryad.g79cnp628) | AE hits and waveforms | Heat-flux monitoring from thresholded transient AE events | Good for testing discontinuous-event sequence models. |
| [Hydrophone heat-flux dataset](https://datadryad.org/dataset/doi:10.5061/dryad.q573n5tvq) | Continuous hydrophone data | Acoustic heat-flux regression | Includes interpolated heat-flux labels and raw synchronized thermal data. |
| [Boiling hysteresis multimodal dataset](https://datadryad.org/dataset/doi:10.5061/dryad.ksn02v7h2) | Hydrophone, microphone, AE | Comparing acoustic signatures across a CHF boiling cycle | Useful for transient regime transitions and hysteresis studies. |
| [Deep learning the sound of boiling](https://data.mendeley.com/datasets/vnnzc7n97m/1) | Audio | Boiling regime classification and advance CHF prediction | Includes raw audio and MATLAB scripts. |
| [NASA DASHlink incipient boiling dataset](https://c3.ndc.nasa.gov/dashlink/resources/1019/) | Accelerometers, visual recordings, metadata | Incipient boiling at local heat leaks | Useful for acoustic-plus-visual detection of nucleation events. |

## Thermal and Infrared Imaging

| Resource | Modality | Best for | Notes |
| --- | --- | --- | --- |
| [Two-phase immersion cooler MOSFET dataset](https://datadryad.org/share/_SEP3K4u6OjIrECuTetxr2AqVoqs5EKJOl8yusAWL8c) | FLIR IR video, thermocouples, CSV hotspot histories | Thermal response and hotspot tracking in two-phase immersion cooling | Includes representative HFE-7100 and water cases, plus flat/microchannel parametric data. |
| [Pool Boiling Dataset](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/6GLGC6) | Thermocouples, calculated heat flux, synchronized image/acoustic data | Relating boiling images and acoustics to heat flux | Not an IR dataset, but provides thermal labels synchronized with optical/acoustic modalities. |
| [Temporal-spatial boiling heat-flux dataset](https://datadryad.org/dataset/doi:10.5061/dryad.6m905qgc7) | Temperature, hydrophone, optical video | Heat-flux labels for transient boiling videos | Useful when thermal measurements are labels rather than primary image data. |

## Reduced-Order Bubble Dynamics

| Tool | Equations or Method | Best for | Notes |
| --- | --- | --- | --- |
| [Bubble-dynamic](https://github.com/BerryWei/Bubble-dynamic) | Rayleigh-Plesset, Keller-Miksis-style modeling | Single-bubble sonoluminescence and acoustic forcing studies | Python/MATLAB code for parameter studies, plotting, and material-property sensitivity. |
| [Bubble_dynamics_simulation](https://github.com/kozakaron/Bubble_dynamics_simulation) | ODE bubble dynamics, parameter sweeps, optimization | Sonochemistry-style single-bubble dynamics | Deprecated in favor of the author's C++ implementation, but still useful as tutorial material. |
| [Bubble_dynamics_simulation_CPP](https://github.com/kozakaron/Bubble_dynamics_simulation_CPP) | C++ bubble dynamics simulation | Higher-performance successor to the Python tutorial repo | Prefer this for new work when the model assumptions match. |
| [bubble-dynamics-resnet](https://github.com/comp-physics/bubble-dynamics-resnet) | Rayleigh-Plesset ODE data + multiscale ResNets | Learning fast time-steppers for bubble ODE integration | Archived; useful as a compact reference for neural ODE-surrogate experiments. |
| [Basilisk Rayleigh-Plesset test](https://basilisk.fr/src/test/bubble.h) | Rayleigh-Plesset comparison test | Solver verification and pressure-driven bubble response | Good for verifying interface-resolved simulations against reduced-order behavior. |

## CFD and Multiphase Simulation

| Tool | Method | Best for | Notes |
| --- | --- | --- | --- |
| [Basilisk](https://basilisk.fr/) | Adaptive finite-volume/VOF framework | Interface-resolved bubbles, droplets, breakup, coalescence, AMR studies | Strong for custom research solvers and benchmark cases; uses Basilisk C. |
| [Aphros](https://github.com/cselab/aphros) | C++ finite-volume, PLIC VOF, Multi-VOF | Large-scale bubbles, foams, coalescence, surface-tension flows | Includes examples such as bubble coalescence, trapped bubbles, bubble jump-off, and foaming flows. |
| [OpenFOAM](https://www.openfoam.org/) | Finite-volume CFD toolbox | VOF and Eulerian multiphase workflows | Relevant solvers include `interFoam`, `multiphaseInterFoam`, and `multiphaseEulerFoam`; good for applied bubble columns and engineering geometries. |
| [OpenFOAM interFoam guide](https://www.openfoam.com/documentation/guides/v1912/doc/guide-applications-solvers-multiphase-interFoam.html) | VOF solver documentation | Two incompressible immiscible fluids | Starting point for rising-bubble and free-surface examples. |
| [OpenFOAM bubble column / dispersed multiphase guide](https://openfoam.org/guides/disperse-multiphase-flows/) | Eulerian multiphase | Dispersed bubbles, bubble columns, industrial multiphase flows | More appropriate when bubbles are modeled as dispersed phases rather than resolved interfaces. |
| [MFiX](https://mfix.netl.doe.gov/mfix/) | TFM, DEM, PIC, hybrid multiphase models | Gas-solid multiphase systems and bubbling fluidized beds | Not liquid-vapor bubble-specific, but valuable for "bubble" structures in fluidized beds. |
| [FluidX3D](https://github.com/ProjectPhysX/FluidX3D) | GPU lattice Boltzmann | Fast CFD prototyping and high-throughput flow simulation | Check multiphase-model maturity and validation before using for boiling or phase-change claims. |
| [JumpingBubbles](https://github.com/comphy-lab/JumpingBubbles) | Basilisk C, VOF, AMR | Coalescence-induced jumping bubbles on substrates | Complete simulation and post-processing framework for bubble coalescence/jump-off phenomena. |
| [Viscoelastic Worthington jets and droplets produced by bursting bubbles](https://github.com/comphy-lab/Viscoelastic-Worthington-jets-and-droplets-produced-by-bursting-bubbles) | Basilisk-based VOF | Bursting bubbles in viscoelastic liquids | Useful for bubble bursting, jets, droplets, and rheology-sensitive interfacial flows. |

## Scientific Machine Learning

| Tool | Task | Best for | Notes |
| --- | --- | --- | --- |
| [BubbleML](https://github.com/HPCForge/BubbleML) | Dataset loading, visualization, FNO examples | Operator learning and optical-flow benchmarks for boiling | Includes notebooks and documentation for data fields and model training. |
| [BubbleML 2.0](https://huggingface.co/datasets/hpcforge/BubbleML_2) | Forecasting data | Transformer and neural-PDE forecasting | Large HDF5 dataset; use streaming or subset downloads where possible. |
| [Bubbleformer](https://huggingface.co/hpcforge/Bubbleformer) | Long-horizon boiling forecasting | Stable multiphase dynamics prediction | Follow-up work to BubbleML 2.0. |
| [BubbleNet](https://github.com/hanfengzhai/BubbleNet) | Physics-informed neural network | Micro-bubble dynamics and inferred flow fields | Combines learned dynamics with physics-informed loss terms. |
| [bubble-dynamics-resnet](https://github.com/comp-physics/bubble-dynamics-resnet) | Learned ODE time-stepping | Rayleigh-Plesset acceleration experiments | Archived but instructive for multiscale residual time-steppers. |
| [FluidNexus](https://github.com/ueoo/FluidNexus) | Reconstruction and prediction from video | Visual-to-dynamics pipelines | Consider as a template for bubble video reconstruction, with domain adaptation and validation. |

## General Image and Flow Analysis Utilities

These are not bubble-specific, but they are often useful in bubble experiments.

| Tool | Best for | Notes |
| --- | --- | --- |
| [OpenPIV](https://github.com/OpenPIV/openpiv-python) | Particle image velocimetry in Python | Useful when tracer-particle velocity fields are needed around bubbles. |
| [PIVlab](https://www.pivlab.de/) | MATLAB PIV with GUI | Practical for quick optical-flow/PIV analysis and teaching workflows. |
| [Trackpy](https://github.com/soft-matter/trackpy) | Particle tracking in Python | Can help with bubble centroids if segmentation is handled upstream. |
| [scikit-image](https://scikit-image.org/) | Classical image processing | Thresholding, morphology, labeling, contour extraction, region properties. |
| [ImageJ/Fiji](https://imagej.net/software/fiji/) | Image inspection and manual/semiautomated analysis | Useful for annotation QA, frame inspection, and simple batch workflows. |
| [napari](https://napari.org/) | Multidimensional image viewing and annotation | Useful for video stacks, masks, and interactive review of segmentation results. |
| [LabelMe](https://github.com/wkentaro/labelme) | Manual annotation | Used by BubbleID-style workflows for liquid-vapor interface labels. |

## Adjacent or Name-Collision Projects

| Project | Why it is listed separately |
| --- | --- |
| [bubblemask](https://github.com/JackEdTaylor/bubblemask) | Despite the name, this is a psychology/vision package for applying Gaussian "Bubbles" masks to image stimuli, not a fluid bubble dynamics tool. |

## Contributing

Pull requests should add entries that are directly useful for bubble dynamics research. Please include:

- A stable link to the code, dataset, paper, or documentation.
- One sentence on the physical regime: boiling vapor bubbles, gas-liquid bubbles, cavitation/sonochemistry, fluidized-bed bubbles, foam, or general multiphase flow.
- Modalities covered: optical, acoustic, AE, thermal/IR, CFD fields, or reduced-order ODEs.
- Reproducibility details when known: license, data size, language, dependencies, pretrained weights, example notebooks, and validation cases.

Suggested entry format:

```markdown
| [Name](link) | Modality or method | Best for | Short notes |
```

## Verification Notes

- GitHub, Dryad, Dataverse, Mendeley, Hugging Face, PyPI, and project documentation pages were checked on 2026-05-21.
- Some large datasets and peer-review sharing links may have access or download limits. Record exact dataset versions and checksums in any downstream project that depends on them.
- CFD entries should not be treated as validated for a new boiling regime without mesh-independence, wall/contact-angle treatment, phase-change model, property model, and experimental validation checks.
