# Low Frequency Voltage Amplifier (SMT Design) 🔊

![Type](https://img.shields.io/badge/Type-Analog%20Circuit-orange)
![Tool](https://img.shields.io/badge/Tool-Cadence%20OrCAD%20%2F%20Allegro-blue)
![Standard](https://img.shields.io/badge/Standard-IPC--2221A-green)

## 1. Project Overview
This project involves the complete design cycle of a **Low Frequency Voltage Amplifier**, designed to meet strict electrical and mechanical constraints. The module is implemented using **SMT (Surface Mount Technology)** on a double-layer PCB, following IPC industry standards.

The design targets a specific set of parameters (Variable $N=29$) and includes schematic design, SPICE simulation, and professional PCB layout.

## 2. Technical Specifications (N=29)
The amplifier was designed to meet the following requirements derived from the project datasheet:

| Parameter | Formula | Calculated Value | Unit |
| :--- | :--- | :--- | :--- |
| **Input Signal ($u_{in}$)** | $50 \times N$ | **1450** (1.45V) | mV |
| **Load Resistance ($R_L$)** | $5 \times N$ | **145** | $\Omega$ |
| **Input Resistance ($R_i$)** | $> 0.1$ | **> 100** |k $\Omega$ |
| **Output Resistance ($R_o$)** | $< 0.1 \times N$ | **< 2.9** | $\Omega$ |
| **Voltage Gain ($A_v$)** | Fixed | **10** | V/V |
| **Operating Temp** | $0 - 70$ | **0 - 70** | $^\circ$ C |

## 3. Design & Implementation Details

### A. Schematic & Simulation
The circuit topology was selected to ensure stability and low distortion within the operating temperature range.
* **Simulation Tool:** TINA-TI / OrCAD PSpice.
* **Verification:** Transient analysis and frequency response (Bode plot) were performed to validate the Gain ($A_v=10$) and Bandwidth.
* **Safety:** All components were calculated to operate within safe limits ($I_{Cmax}$, $V_{CEmax}$, $P_{dmax}$).

### B. PCB Layout Specifications
The physical design was executed in **Cadence OrCAD PCB Editor**, adhering to strict manufacturing constraints:

* **Board Dimensions:** $40\text{mm} \times 40\text{mm}$.
* **Material:** FR4, Double Layer, 1.6mm thickness, 18µm copper.
* **Placement:** All SMT components (0805 packages, SOT-23) placed on the **TOP Layer**.
* **Mechanical:** Includes fiducial markers for automated assembly and a strict 1mm edge clearance.

### C. Signal Integrity & Power Design
To ensure signal quality and thermal management, trace widths were calculated based on current capacity:
* **Ground(GND):** 26 mil.
* **Input+Alimentation(V+, V-, Vin and Vout):** 18 mil.
* **Signal Traces:** 16 mil.
* **Clearance/Spacing:** 14 mil globally.

## 4. Project Structure
The repository is organized to facilitate manufacturing and review:

```text
├── Layout/          # Cadence PCB file + Gerber and Excellon files (.brd, .art and .drl)
├── Schematics/            # TINA-TI Schematics(.tsc)
├── Simulations/           # Bode plots and Waveforms
├── docs/                  # Documentation & Visuals
│   ├── schematic.png      # Detailed Circuit Diagram
│   ├── pcb_layout_2d.png # 2D View of Top Layer
│   ├── pcb_3D_view.png    # 3D Rendering of the module
│   ├── Simulations/       # Bode plots and Waveforms
│   └── bill_of_materials.pdf
└── README.md
