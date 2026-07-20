# Project Dopamine
### Computational Modeling of Reward Dysregulation and Beneficial Reward Engineering in Spiking Neural Networks

**Status:** Active — Phase 3 complete, strengthening experimental rigor for publication  
**Author:** Ishita, Undergraduate ECE Student...  
**Framework:** Brian2 (Python), neuromorphic computing context  

---

## Overview

Project Dopamine is an independent undergraduate research project modeling 
dopamine dysregulation and reward sensitivity in spiking neural networks 
(SNNs). The project emerged from connecting reward prediction error theory 
(Schultz et al., 1997) to the neuroscience of attention dysregulation, 
then grounding these dynamics in neuromorphic computing design principles.

The central question: **can we engineer a reward schedule for a neuromorphic 
agent that achieves high engagement without producing sensitivity collapse?**

The answer, established across four phases: **yes — and the parameters are 
precisely quantifiable.**

---

## Core Findings

**Phase 1 — Characterization (notebook 13)**
A system exposed to engineered high-frequency variable rewards (50-150ms 
intervals) becomes **3x less sensitive** to identical stimuli than a healthy 
system on spaced rewards (500ms intervals), measured via binary spike 
detection across 10 test points.

**Mechanistic foundation (notebook 14)**
Synaptic consolidation explains why dysregulation resists recovery — fast 
plastic changes become embedded in a slow stable component that resists 
active reversal signals completely, even after 2x the original training 
duration.

**Phase 2 — Recalibration (notebook 15)**
Recovery from dysregulation takes **5.9x longer** than dysregulation onset 
under identical conditions (88ms to dysregulate vs 513ms to recover). 
Homeostatic plasticity provides no meaningful benefit (timescale mismatch). 
Intervention timing shows negligible effect within this model's equilibrium 
dynamics.

**Phase 3 — Beneficial Reward Engineering (notebook 16)**
A systematic sweep of 35 reward schedule parameter combinations identifies 
an optimal operating point: **200ms mean interval, variability σ=0.9×mean**. 
This achieves:
- 78% of dysregulated engagement (38 vs 49 spikes)
- 2.09x better sensitivity preservation than dysregulating schedule
- 2.00x more engagement than conservative healthy schedule
- Sensitivity maintained within healthy bounds throughout

A counterintuitive finding: at moderate intervals (200ms), HIGH variability 
preserves sensitivity better than low variability — because unpredictable 
timing occasionally produces recovery gaps that fixed schedules cannot.

---

## Repository Structure
project-dopamine/
├── notebooks/          ← core simulation notebooks (phases 1-3)
├── experiments/        ← multi-seed rigorous experimental runs
├── figures/            ← publication-quality figures
└── papers/             ← literature informing this work

---

## Notebooks

### 13 — Phase 1: Dopamine Dysregulation
Two parallel systems exposed to different reward schedules. Quantifies 
sensitivity divergence via adaptive threshold modeling and binary 
spike detection.

### 14 — Synaptic Consolidation
Two-stage synapse model demonstrating transition from plastic short-term 
to stable long-term memory. Explains structural basis of dysregulation 
resistance.

### 15 — Phase 2: Recalibration & Intervention
Three recovery strategies tested from dysregulated baseline. Quantifies 
5.9x hysteresis ratio. Documents two honest null results: homeostatic 
plasticity and intervention timing.

### 16 — Phase 3: Beneficial Reward Engineering
35-condition parameter sweep producing a reward schedule design map. 
Head-to-head validation of optimal condition against dysregulated and 
healthy baselines.

---

## Neuromorphic Computing Context

This work is directly relevant to neuromorphic RL agent design on hardware 
like Intel's Loihi 2. When reward signals are programmable parameters 
(as they are in neuromorphic systems), the design map produced here provides 
quantitative guidance for engineers: intervals below 200ms risk sensitivity 
collapse regardless of variability; intervals of 200-400ms with moderate-to-high 
variability maintain healthy sensitivity while maximizing engagement.

The adversarial reward hacking problem in RL — where environments are 
engineered to maximize reward frequency — maps directly onto the dysregulation 
mechanism characterized here, providing a principled basis for minimum 
reward interval constraints in hardware implementations.

---

## Current Status & Next Steps

- [x] Phase 1: Characterization complete
- [x] Synaptic consolidation mechanistic foundation
- [x] Phase 2: Recalibration & intervention complete  
- [x] Phase 3: Beneficial reward engineering complete
- [ ] Multi-seed validation (30 runs per condition, error bars)
- [ ] Statistical significance testing across conditions
- [ ] Extended parameter sweep (finer resolution, tau_adapt as third parameter)
- [ ] Paper draft targeting arXiv (cs.NE) and ICONS workshop

---

## Dependencies
brian2
numpy
matplotlib
jupyter

Install: `pip install brian2 numpy matplotlib jupyter`

---

## Citation

If referencing this work, please cite:  
Kokate, I. (2026). *Project Dopamine: Computational Modeling of Reward 
Dysregulation and Beneficial Reward Engineering in Spiking Neural Networks*. 
Undergraduate independent research project, TCET Mumbai.  
GitHub: github.com/ishitakokate/project-dopamine
