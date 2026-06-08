# Flyback Transformer Verifier

**Version:** 1.1  
**Status:** Active  
**Type:** Offline single-file HTML tool — no installation, no internet required after download

## What it does

Verifies a flyback / SMPS transformer design against datasheet 
specifications and physical sample measurements. Covers:

- Operating conditions and design parameter entry
- Core geometry with Chinese vendor material presets
  (TDK N87/N97/PC95, Ferroxcube 3C95, DMEGC DMR44, 
  Hengdian R10000, KMnetics TP4A)
- Winding configuration with per-strand AWG calculator 
  and skin-depth check
- Datasheet reference values with dot polarity assignments
- **Design verification:** Bmax, duty cycle, Vds/Vdiode stress, 
  leakage ratio, Al consistency, window utilization
- **Sample inspection:** Lp, Llk, Rdc, turns ratio, 
  dot polarity (primary / secondary / auxiliary), 
  hipot, isolation resistance, visual checklist
- **Measurement guide:** step-by-step LCR procedure with 
  wiring diagrams for every measurement, dot polarity 
  test method explained for all windings
- Verification report with JSON export/import and print-to-PDF

## How to use

**Option A — Use online (GitHub Pages):**  
👉 [Open tool](https://your-username.github.io/engineering-tools/tools/flyback-transformer-verifier/)

**Option B — Use offline:**  
Download `index.html` → open in any browser → works with no internet connection.  
All data stays on your machine. Nothing is sent anywhere.

## Tested on

Chrome 120+, Firefox 121+, Edge 120+

## Changelog

See [CHANGELOG.md](./CHANGELOG.md)
