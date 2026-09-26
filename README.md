# 4 Stage NMOS Amplifier Design

A low-power, multi-stage MOSFET amplifier designed and simulated in KiCad to meet specified gain, bandwidth, output swing, loading, and power constraints using a 3.3 V single supply.

## Requirements

- DC supply: 3.3 V
- Total unloaded gain: > 60 dB
- Load sensitivity gain reduction: < 10%
- Gain per stage: < 40 dB
- Bandwidth: > 500 kHz
- Output swing: > 1.5 Vpp
- Input resistance: > 100 kΩ
- Load: 10 kΩ || 2 pF
- Maximum branch current: 200 µA
- Total DC power: < 1 mW
- MOSFET channel length: 0.5–5 µm
- Overdrive voltage: 0.2–0.6 V

The final design uses multiple common-source (CS) amplifier stages followed by a MOSFET buffer to provide sufficient gain while maintaining low power consumption and reducing load sensitivity.

## Design Methodology
The design was developed through hand calculations followed by iterative KiCad simulations. The procedure was as follows:

1. Select a common DC bias point for the amplifier stages.
2. Determine the number of stages needed to meet the total gain requirement and amplifier type.
3. Select drain current and resistor values based on gain and power constraints.
4. Design high-resistance gate bias networks to maintain the required input resistance.
5. Select NMOS W/L ratios based on the desired operating points.
6. Select coupling capacitors to meet the bandwidth requirement.
7. Add and optimize the output buffer for load sensitivity and output swing.
8. Iterate initial component values based on simulation results.

Some hand calculations are present at the root of the repository. The changes made due to initial calculations include:
- 2 stage design to 3 stage design due to unmet gain and power constraints.
- Re-selection of bias voltages/over drive voltages due to higher power draw.
- Higher capacitance values caused bandwidth issues.

## Simulation Results
From the initial simulation results and steps in between, the following changes were made:

- Input Capacitor: The initial 1 nF capacitor resulted in a high low-frequency cutoff. Increasing it to 10 nF reduced the cutoff to approximately 1 kHz.
- Buffer Bias: The calculated buffer bias produced only about 70 µA of drain current, resulting in insufficient output bias voltage. The bias resistors were adjusted to increase the current to approximately 100 µA.
- Buffer Sizing: The buffer NMOS W/L ratio was increased from 25 to 200.

Some results of the simulations are shown below:

