# SFS-FVM: Spectral Flux-Shaping Finite-Volume Method

> **A high-order numerical scheme reconciling low dispersion/dissipation for acoustics with robust shock-capturing capabilities.**

## Overview

Accurate prediction of flow-generated noise requires numerical schemes that can propagate waves with minimal error while handling shocks without crashing. **SFS-FVM (Spectral Flux-Shaping Finite-Volume Method)** addresses this challenge by introducing a novel flux-shaping technique within a standard conservative framework.

This project implements SFS-FVM applied to standard upwind flux-splitting schemes (e.g., **Roe**, **AUSM+up**). By separating the numerical flux into distinct **transport** and **diffusive** paths, the method independently optimizes dispersion and dissipation errors.

## Key Features

- **Spectral Flux-Shaping:** Applies compact Padé operators to the transport path to significantly correct dispersion errors.
- **Zero Pass-Band Dissipation (ZPD):** Completely eliminates numerical damping for well-resolved waves in smooth flow regions.
- **Shock Robustness:** Features a sensor-based gating mechanism that smoothly reverts to the baseline shock-capturing scheme near discontinuities, ensuring nonlinear stability.
- **Conservative Formulation:** Built upon the standard Finite Volume Method (FVM), ensuring strict conservation of mass, momentum, and energy.

## Methodology

The core strategy involves splitting the numerical flux into two distinct paths:

1. **Transport Path:** Shaped using a bounded Padé filter to cancel dispersion errors.
2. **Diffusive Path:** Controlled by a spectral bump function to enforce **ZPD** while maintaining high-wavenumber stability.

This approach allows the scheme to behave like a high-fidelity central scheme in smooth regions and a robust upwind scheme near shocks.

## Validation Cases & Results

The code has been validated against canonical test cases, demonstrating superior performance over baseline solvers.

### 1. Fundamental Wave Propagation
- **1-D Gaussian Advection:** Verifies extremely low dispersion characteristics.
- **2-D Pulse Propagation (Tam & Webb Benchmark):** Demonstrates isotropy and the preservation of acoustic, entropy, and vorticity pulses in a mean flow.

### 2. Shock-Capturing Capabilities
- **Sod Shock Tube:** Verifies stable capturing of shocks and contact discontinuities.
- **Shu-Osher Problem:** Validates the accurate interaction between shocks and entropy waves.

---

## Code Availability

The source code for this project is **available upon request**.
Due to ongoing research and copyright considerations, the full implementation is not publicly archived in this repository.

Researchers interested in the code for academic or review purposes may contact the author directly.

## Authors

* **Chanho Park** (GIST)
* **Yeachan Kwak** (GIST)
* **Seongim Choi** (GIST)
* **Ray-Sing Lin** (GIST)


*School of Mechanical Engineering, Gwangju Institute of Science and Technology (GIST), Republic of Korea*
