# A Spectral Flux-Shaping Finite-Volume Method (SFS-FVM)

Implementation of the **Spectral Flux-Shaping Finite-Volume Method (SFS-FVM)**, a novel high-order numerical scheme designed for Computational Aeroacoustics (CAA) and compressible flows with shocks.

This framework reconciles the conflicting requirements of **low dispersion/dissipation** for acoustic waves and **robust stability** for discontinuities (shocks) within a conservative finite-volume context.

---

## Overview
Accurate prediction of flow-generated noise requires numerical schemes that can propagate waves with minimal error while handling shocks without crashing. 
This project introduces **SFS-FVM**, which separates the numerical flux into distinct **transport** and **diffusive** paths to independently optimize dispersion and dissipation errors.

## Key Features
* **Spectral Flux-Shaping:** Applies compact Padé operators to numerical fluxes to correct dispersion errors.
* **Zero Pass-Band Dissipation (ZPD):** Completely eliminates numerical damping for well-resolved waves in smooth flow regions.
* **Shock Robustness:** Features a sensor-based gating mechanism that smoothly reverts to the baseline shock-capturing scheme (e.g., Roe, AUSM+up) near discontinuities.
* **Conservative Formulation:** Built upon standard Finite Volume Method (FVM) ensuring conservation of mass, momentum, and energy.

## Methodology
The core strategy involves splitting the numerical flux into two paths:
1.  **Transport Path:** Shaped using a bounded Padé filter to cancel dispersion errors.
2.  **Diffusive Path:** Controlled by a spectral bump function to enforce ZPD (Zero Pass-Band Dissipation) while maintaining high-wavenumber stability.

This approach allows the scheme to behave like a high-fidelity central scheme in smooth regions and a robust upwind scheme near shocks.

## Validation Cases
The code has been validated against several canonical test cases:
* **1-D Linear Advection:** Gaussian wave packet propagation (checking low dispersion).
* **2-D Acoustic Scattering:** Scattering off a cylinder (demonstrating ZPD and isotropy).
* **Shock Tube Problems:** Sod shock tube & Shu-Osher problem (verifying shock capturing).

---

## Code Availability
The source code for this project is available upon request. Due to ongoing research and copyright considerations, the full implementation is not publicly archived here.

Researchers interested in the code for academic or review purposes may contact the author directly.

## Authors
* **Chanho Park**, **Yeachan Kwak**, **Seongim Choi**, **Ray-Sing Lin**
* Gwangju Institute of Science and Technology (GIST), Republic of Korea

## Reference
* *Manuscript submitted to Journal of Computational Physics (2025)*

## Contact
For code access or inquiries:
**Chanho Park** xvegaasd@gm.gist.ac.kr
