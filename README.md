# 7nm-FINFET-Circuit-Simulation
# FinFET-Based Inverter and Bandgap Reference Analysis using ngspice

## Overview
This project explores FinFET device behavior and circuit-level performance
using ngspice simulations. The work begins with a theoretical study of device
scaling and FinFET motivation, followed by practical analysis of a FinFET-based
inverter and a bandgap reference circuit.

An open-source FinFET SPICE deck was used as the base and modified to study
various electrical and performance parameters.

---

## Background Study
- Zeta scaling and limitations of CMOS planar devices
- Motivation for FinFET technology at advanced nodes
- Basic FinFET structure and layout concepts
- Comparison between planar CMOS and FinFET devices

---

## Tools & Technology
- ngspice
- xschem
- Open-source FinFET SPICE models

---

## FinFET Inverter Analysis

### Methodology
- Used a FinFET inverter SPICE deck
- Modified **channel width (W)** and **channel length (L)** of:
  - n-FinFET, having Nfin = 14
  - p-FinFET, having Pfin = 12
- Performed DC and AC simulations to evaluate inverter behavior

### FINFET based Inverter spice deck
```
**.subckt inverter_vtc
Xpfet1 nfet_out nfet_in vdd vdd asap_7nm_pfet l=7e-009 nfin=12
Xnfet1 nfet_out nfet_in GND GND asap_7nm_nfet l=7e-009 nfin=14
V1 nfet_in GND pulse(0 0.7 20p 10p 10p 20p 500p 1)
V2 vdd GND 0.7
```

### Parameters Analyzed
- Voltage Transfer Characteristics (VTC)
  ![Inverter VTC](/images/Inverter_VTC.png)
  ```
.subckt inverter_vtc
Xpfet1 nfet_out nfet_in vdd vdd asap_7nm_pfet l=7e-009 nfin=12
Xnfet1 nfet_out nfet_in GND GND asap_7nm_nfet l=7e-009 nfin=14
V1 nfet_in GND pulse(0 0.7 20p 10p 10p 20p 500p 1)
V2 vdd GND 0.7
```

- Drain current (Id)
- Power consumption
- Propagation delay
- Gain
- Noise margin
- Transconductance (gm)
- Frequency response

### Key Observations
- Improved gain and noise margins compared to planar CMOS
- Reduced short-channel effects
- Better switching characteristics due to FinFET electrostatic control

---

## Bandgap Reference Circuit

### Circuit Description
A FinFET-based bandgap reference circuit was implemented using a provided
circuit topology. To introduce a unique design variation, the resistor value
in the biasing network was modified.

### Unique Design Choice
- Bias resistor value set to **448 Ω**
- Value derived from the **ASCII representation** to ensure design uniqueness

---

### DC Analysis
- Performed DC sweep to observe reference voltage (Vref)
- Studied variation of output voltage with:
  - Supply voltage (VDD)
  - Temperature

### Transient Analysis
- Startup behavior of the bandgap reference was analyzed
- Startup time and stability were observed using transient simulations

### Performance Metrics Recorded
- Reference voltage stability
- Line regulation (VDD variation)
- Temperature dependence
- Startup behavior

---
## Credits
This work is based on an open-source FinFET SPICE model and inverter deck
sourced from GitHub.

Full credit is given to the original contributors:
-ahdvakd
-ygfagj
