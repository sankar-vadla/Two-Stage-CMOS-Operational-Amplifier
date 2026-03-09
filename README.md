# Two-Stage CMOS Operational Amplifier

## Overview
This repository contains the transistor-level design and LTspice simulation files for a 1.8V Two-Stage CMOS Operational Amplifier with a source-follower output buffer. The project focuses on fundamental analog VLSI design principles, specifically addressing systematic offset correction through current density scaling and AC stability via Miller frequency compensation.

This project was developed as part of a core analog IC design portfolio.

## Key Performance Specifications
| Parameter | Value | 
| :--- | :--- |
| **Technology / Supply Voltage** | 1.8V |
| **Open-Loop DC Gain** | 117 dB |
| **Unity Gain Bandwidth (UGB)** | 631.8 kHz |
| **Phase Margin** | 40.5° |
| **Slew Rate** | 0.81 V/µs |
| **Compensation Capacitor ($C_c$)** | 10 pF |
| **Load Capacitor ($C_{load}$)** | 10 pF |

## Design Highlights
* **DC Biasing & Offset Correction:** Eliminated railed output conditions by tracing systematic offsets in the current mirrors. Scaled the W/L ratios of the common-source amplification stage to perfectly match the current density of the differential pair, ensuring all MOSFETs operate deep in the saturation region with an output resting voltage of ~0.76V.
* **Frequency Compensation:** Implemented a 10 pF Miller capacitor across the high-gain stage to establish a dominant pole. This intentionally traded excess bandwidth for a highly stable phase margin of 40.5°, preventing oscillation in closed-loop configurations.
* **Large-Signal Transient Response:** Verified slew rate and step response by wiring the amplifier in a closed-loop unity-gain buffer configuration and driving it with a sharp 0.4V to 1.4V square wave pulse. 

## Simulation Results
*(Note: Upload your screenshot images to your GitHub repo, then update the file names below to display them here!)*

### 1. Complete Schematic
![Op-Amp Schematic](circuit_diagram.pdf)
*Complete circuit diagram including the differential pair, common-source stage, and output buffer.*

### 2. AC Analysis (Bode Plot)
![Bode Plot](bode_plot.pdf)
*Open-loop frequency response showing 117 dB gain and smooth -20dB/decade roll-off.*

### 3. Transient Analysis (Slew Rate)
![Transient Response](transient_response.pdf)
*Closed-loop step response showing a slew rate of 0.81 V/µs with minimal overshoot.*

## How to Run the Simulations
1. Download and install [LTspice](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html).
2. Clone this repository and open `twostage_opamp.asc` in LTspice.
3. The schematic contains three pre-written SPICE directives:
   * `.op` (DC Operating Point)
   * `.ac dec 100 1 100Meg` (AC Analysis for Gain/Phase)
   * `.tran 0 10u` (Transient Analysis for Slew Rate)
4. Ensure only **one** directive starts with a period (`.`) at a time. Comment out the others by changing the period to a semicolon (`;`).
5. Click the **Run** (running person) icon to execute the active simulation.

## Tools Used
* **LTspice:** Transistor-level schematic capture and SPICE simulation.
