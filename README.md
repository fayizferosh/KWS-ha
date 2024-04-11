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


| :exclamation: Important Note            |
|-----------------------------------------|

## Forked from the Caravel User Project 

Refer to [README](docs/source/index.rst#section-quickstart) for a quickstart of how to use caravel_user_project

Refer to [README](docs/source/index.rst) for this sample project documentation. 

Refer to the following [readthedocs](https://caravel-sim-infrastructure.readthedocs.io/en/latest/index.html) for how to add cocotb tests to your project. 
