![MelKWS_Engine](https://github.com/fayizferosh/KWS-ha/assets/63997454/40d1d8ac-4fe3-462d-9c74-2bc775a91723)
# MelKWS Engine

![Static Badge](https://img.shields.io/badge/OS-linux-orange)
![Static Badge](https://img.shields.io/badge/EDA%20Tools-OpenLANE-navy)
![Static Badge](https://img.shields.io/badge/languages-verilog%2C_bash%2C_TCL-crimson)
![GitHub last commit](https://img.shields.io/github/last-commit/fayizferosh/KWS-ha)
![GitHub language count](https://img.shields.io/github/languages/count/fayizferosh/KWS-ha)
![GitHub top language](https://img.shields.io/github/languages/top/fayizferosh/KWS-ha)
![GitHub repo size](https://img.shields.io/github/repo-size/fayizferosh/KWS-ha)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/fayizferosh/KWS-ha)
![GitHub repo file count (file type)](https://img.shields.io/github/directory-file-count/fayizferosh/KWS-ha)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![UPRJ_CI](https://github.com/efabless/caravel_project_example/actions/workflows/user_project_ci.yml/badge.svg)](https://github.com/efabless/caravel_project_example/actions/workflows/user_project_ci.yml) [![Caravel Build](https://github.com/efabless/caravel_project_example/actions/workflows/caravel_build.yml/badge.svg)](https://github.com/efabless/caravel_project_example/actions/workflows/caravel_build.yml)
<!---
Comments
-->

> A simple and resource efficient hardware accelerator designed specifically for Keyword Spotting (KWS) applications using log-mel spectrograms as the audio feature extractor.

## Architecture

### Description
1. Input:
    - The input audio stream is sampled at a specific frequency, such as 16 kHz.
    - Each audio frame consists of a fixed number of samples.

2. Log-Mel Spectrogram Computation:
    - Implement a lightweight log-mel spectrogram computation module to extract features from the input audio stream.

3. Keyword Detection:
    - The accelerator should detect the presence or absence of a single predefined keyword or command based on the computed log-mel spectrograms.

4. Output:
    - Provide a mechanism to indicate the presence or absence of the keyword in the input audio stream.
    - Output a binary flag signal indicating the presence or absence of the keyword.
  
### Architecture Choice

1. **Input Interface:**
    - _Purpose:_ Handles incoming audio samples, ensuring they are correctly timed and formatted for processing.
    - _Components:_
        - _Sample buffer:_ Temporarily stores incoming audio samples.
        - _Control logic:_ Manages the flow of samples based on system state and input validity. 
2. **Pre-processing:**
    - _Purpose:_ Applies necessary pre-processing steps to the audio samples, such as framing and windowing.
    - _Components:_
        - _Frame buffer:_ Segments the continuous audio stream into overlapping frames.
        - _Window function:_ Applies a windowing function to each frame to minimize spectral leakage.
3. **FFT Module:**
    - _Purpose:_ Converts time-domain audio frames into frequency-domain representations using the Fast Fourier Transform (FFT).
    - _Components:_
        - _FFT processor:_ Computes the FFT of each windowed frame.
4. **Mel Filterbank Processing:**
    - _Purpose:_ Applies a set of Mel-scaled filters to the FFT output to extract frequency bands that mimic human auditory perception.
    - _Components:_
        - _Filterbank:_ A collection of band-pass filters corresponding to the Mel scale.
        - _Energy computation:_ Calculates the energy in each Mel band.
5. **Feature Extraction:**
    - _Purpose:_ Optionally extracts additional features from the Mel spectrogram, such as MFCCs (Mel Frequency Cepstral Coefficients), if required by the keyword detection logic.
    - _Components:_
        - _Feature extractor:_ Calculates MFCCs or other features from the Mel spectrogram.
6. **Dynamic Precision Adjustment:**
    - _Purpose:_ Adjusts the precision of the FFT or Mel spectrogram data to optimize for computational efficiency or resource usage.
    - _Components:_
        - _Precision control:_ Dynamically adjusts data bit-width based on configurable criteria.
7. **Logarithmic Compression:**
    - _Purpose:_ Applies logarithmic compression to the Mel spectrogram to better match the non-linear perception of loudness in the human auditory system.
    - _Components:_
        - _Logarithmic function:_ Computes the logarithm of Mel spectrogram values.
8. **Keyword Detection Logic:**
    - _Purpose:_ Analyzes the log-Mel spectrogram (and possibly additional features) to detect the presence of specific keywords.
    - _Components:_
        - _Detection algorithm:_ Implements a simple thresholding or a more complex pattern matching/machine learning algorithm to identify keywords.
        - _Keyword selector:_ Allows dynamic selection of the keyword(s) to be detected.
9. **Output Interface:**
    - _Purpose:_ Indicates the detection result, such as the presence of a keyword.
    - Components:
        - Detection output: Signals when a keyword has been detected.
        - Status indicators: Provide additional information about the detection process, such as confidence levels.
10. **Integration and Control (Top):**
    - _System Controller:_ Coordinates the operation of all stages, managing state transitions, processing flow, and synchronization.
    - _Clock and Reset Management:_ Ensures all components operate synchronously and can be reset to a known state.

| :exclamation: Important Note            |
|-----------------------------------------|

## Forked from the Caravel User Project 

Refer to [README](docs/source/index.rst#section-quickstart) for a quickstart of how to use caravel_user_project

Refer to [README](docs/source/index.rst) for this sample project documentation. 

Refer to the following [readthedocs](https://caravel-sim-infrastructure.readthedocs.io/en/latest/index.html) for how to add cocotb tests to your project. 
