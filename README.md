# 12V to 5V Step Down Buck Converter (LTSpice & KiCad PCB)
This is an asynchronous buck converter that steps down 12V to 5V, designed and simulates in LTSpice using the LTC4440 (IC) high-side gate driver with a bootstrap circuit.
![KiCad](schematic/KiCad-Screenshot.png#width=100%) ![LTSpice](schematic/LTSpice-Screenshot.png#width=49%)

## Key Specifications
* **Input Voltage ($V_{in}$):** 12V DC
* **Output Voltage ($V_{out}$):** ~4.8V DC (Steady-State)
* **Load Current ($I_{out}$):** 1A (5Ω Load)
* **Switching Frequency ($f_{sw}$):** 100 kHz (41.67% Duty Cycle)
* **Output Ripple ($\Delta V_{out}$):** ~39 mV (< 1%)
* **PCB Architecture:** 2-layer board optimized for high-frequency switching and low EMI

## Design Calculations
* **Duty Cycle:** $D = V_{out} / V_{in} = 5V / 12V = 41.67\%$
* **Inductor:** $L = \frac{(V_{in} - V_{out}) \cdot T_{on}}{\Delta I_L} = \frac{(12 - 5) \cdot 4.17\mu s}{0.3A} \approx 97.3\mu H \rightarrow 100\mu H$
* **High-Side MOSFET Drive:** Utilizes the LTC4440 high-speed driver paired with a bootstrap diode and capacitor ($C_{boot} = 100\text{nF}$) to elevate gate voltage above the floating switching node.

## Simulation & Results
![Transient Waveform](waveform/buck_converter.png)
* **Startup Phase:** Displays natural LC filter settling overshoot peaking at 6.5V.
* **Non-Idealities:** Steady-state output settles slightly below theoretical 5V at 4.8V due to MOSFET $R_

## PCB Layout & Manufacturing
![PCB Render](pcb-layout/asynchronous_buck_converter.png)
* **Compact Switching Loop:** Components positioned to minimize power loop area to reduce parasitic inductance and switching noise.
* **Thermal Management:** Integrated ground plane pours for efficient heat dissipation across components.
* **DRC Verification:** Passed full KiCad Design Rule Checks.

