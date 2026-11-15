# 🔬 Technical Addendums: Mathematical Verification

This directory provides standalone, zero-weight mathematical proofs demonstrating how diffusion solvers sculpt structured imagery from Gaussian noise without external databases or pre-baked assets.

# Verifying `airtight_ddpm_diffusion.py` Locally

This script mirrors the core mathematical solver of a production diffusion pipeline using only **NumPy** and **Pillow**—zero model weights, zero external APIs, and zero image databases:

1. **64-Bit Seed Determinism (`np.random.default_rng`):** Press `[ENTER]` to generate an image from fresh 64-bit OS entropy (`secrets.randbits(64)`), or input any logged integer seed to reproduce the exact pixel array deterministically.
2. **State-Coupled Denoising (`predict_noise`):** At each reverse step, the noise predictor reads both the spatial intent field and the evolving noisy `latents` tensor. Different seeds naturally diverge into distinct micro-textures while preserving the underlying mathematical intent.
3. **Cosine Schedule & DDIM Solver:** Implements the Nichol & Dhariwal cosine variance schedule ($\bar{\alpha}_t$) alongside explicit $x_0$-prediction and dynamic thresholding.

### Quick Start

```bash
pip install numpy pillow
python airtight_ddpm_diffusion.py
```
