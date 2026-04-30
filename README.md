# CellECGNet

**CellECGNet** is a label-free video-based platform for functional phenotyping of cardiomyocyte contraction dynamics.

CellECGNet analyzes bright-field cardiomyocyte contraction videos and extracts motion-derived contraction traces, contraction-cycle landmarks, functional parameters, and phenotype-level outputs. The current release is provided as Windows executable files for demonstration and internal evaluation. Source code will be released after manuscript preparation and code cleanup.

## Current Release Status

- Windows executable: two versions are provided in the release package
  - `CellECGNet-DEFORM`: full version using the DEFORM-Net motion estimation backend
  - `CellECGNet-DIS`: lightweight version using the OpenCV DIS backend for systems that cannot run the DEFORM-Net version
- Source code: pending public release
- Example data: not included in the initial release
- License: to be determined

## Version Selection

Use `CellECGNet-DEFORM` if your system can run the full DEFORM-Net backend. This is the default full version and is recommended when GPU/deep-learning backend support is available.

Use `CellECGNet-DIS` if the DEFORM-Net version cannot run on your system. The DIS version uses the OpenCV Dense Inverse Search backend and is provided as a lightweight compatibility version.

## Main Functions

CellECGNet currently supports:

- Dense motion-field extraction from cardiomyocyte contraction videos
- Automatic ROI mask generation
- ROI motion trace extraction
- State-based contraction cycle analysis
- Detection of contraction-cycle landmarks:
  - Start
  - maximum contraction speed (MCS)
  - contraction-to-relaxation transition (CTS)
  - maximum relaxation speed (MRS)
  - End
- Extraction of contraction functional parameters, including rhythm, timing, amplitude, velocity-related kinetics, waveform morphology, and spatial synchrony
- Rule-based mechanical phenotype screening
- Deep learning-based functional phenotype classification

## Functional Phenotype Output

The current second-layer model classifies videos into three phenotype-level categories:

- `healthy-like`
- `arrhythmia-like`
- `contractile-dysfunction-like`

These outputs are intended for **functional phenotyping and research use**, not for clinical diagnosis.

## How to Use

1. Download the appropriate Windows executable from the release page.
2. Launch the executable:
   - Use `CellECGNet-DEFORM` for the full version.
   - Use `CellECGNet-DIS` if the DEFORM-Net version cannot run on your system.
3. Import cardiomyocyte contraction videos.
4. Run the analysis workflow.
5. Export contraction traces, key-point results, functional parameters, and phenotype-level outputs.

Detailed user documentation will be added in a future release.

## Input Data

CellECGNet is designed for label-free cardiomyocyte contraction videos, such as bright-field or phase-contrast recordings.

Recommended video properties:

- Clear visible contraction activity
- Stable field of view
- Sufficient frame rate for contraction-cycle analysis
- Minimal stage drift and focus instability

## Output Files

Depending on the analysis mode, CellECGNet may export:

- ROI motion traces
- Motion-field summaries
- Contraction-cycle key points
- Cycle-level functional parameters
- Video-level summary parameters
- Rule-based mechanical phenotype labels
- Deep learning phenotype probabilities
- Quality-control plots and reports

## Method Overview

CellECGNet estimates frame-to-frame motion fields from input videos and generates an ROI motion-magnitude trace. The full version uses a DEFORM-Net-based dense motion estimation backend, while the lightweight version uses the OpenCV DIS backend.

Motion-field-derived representations are used for state-based contraction-cycle analysis. Functional parameters are extracted from detected cycle landmarks. A rule-based layer provides interpretable mechanical phenotype screening, and a supervised TCN-BiGRU model performs phenotype-level classification.

## Research Use Only

CellECGNet is currently intended for research use in cardiomyocyte functional analysis, disease modeling, and drug-response studies. The software output should be interpreted as phenotype-level information and should not be used as a clinical diagnostic result.

## Source Code Availability

The source code is currently being cleaned and organized. It will be made publicly available after manuscript preparation and internal validation are completed.

## Citation

A formal citation will be provided after manuscript submission or publication.

## Contact

For questions, please contact the repository owner.
