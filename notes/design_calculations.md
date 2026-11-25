# Design Calculations: 12 V to 5 V DC-DC Buck Converter

## 1. Design Specifications

The following specifications are used for the theoretical design calculations.

| Parameter | Symbol | Value |
|---|---|---|
| Input Voltage | Vin | 12 V |
| Target Output Voltage | Vout | 5 V |
| Switching Frequency | fs | 50 kHz |
| Inductance | L | 220 µH |
| Output Capacitance | C | 220 µF |
| Load Resistance | R | 5 Ω |

The initial calculations assume an ideal buck converter operating in Continuous Conduction Mode (CCM), unless otherwise stated.

## 2. Duty Cycle Calculation

For an ideal buck converter, the duty cycle is given by:

D = Vout / Vin

Substituting the design values:

D = 5 / 12

D = 0.4167

Therefore:

**Ideal Duty Cycle = 41.67%**

This means the switching device must remain ON for approximately 41.67% of each switching period under ideal steady-state conditions.

## 3. Switching Period and ON/OFF Time

The switching period is calculated using:

T = 1 / fs

Substituting:

T = 1 / 50,000

**T = 20 µs**

The ON time is:

Ton = D × T

Ton = 0.4167 × 20

**Ton = 8.333 µs**

The OFF time is:

Toff = (1 - D) × T

Toff = 0.5833 × 20

**Toff = 11.667 µs**

Therefore, the switching cycle consists of:

- ON time: 8.333 µs
- OFF time: 11.667 µs
- Total period: 20 µs

## 4. Output and Load Current

Using Ohm's law:

Iout = Vout / R

Substituting the target values:

Iout = 5 / 5

**Ideal Output Current = 1 A**

For an ideal buck converter operating in CCM, the average inductor current is approximately equal to the output current.

Therefore:

**Average Inductor Current = 1 A**

## 5. Inductor Ripple Current Calculation

The peak-to-peak inductor ripple current for an ideal buck converter is:

ΔIL = ((Vin - Vout) × D) / (L × fs)

Substituting:

ΔIL = ((12 - 5) × 0.4167) / (220 × 10⁻⁶ × 50 × 10³)

**ΔIL ≈ 0.265 A**

Therefore, the expected peak-to-peak inductor current ripple is approximately:

**ΔIL = 265 mA**

The approximate peak and minimum inductor currents are:

IL(max) = Iout + (ΔIL / 2)

IL(max) = 1 + (0.265 / 2)

**IL(max) ≈ 1.133 A**

IL(min) = Iout - (ΔIL / 2)

IL(min) = 1 - (0.265 / 2)

**IL(min) ≈ 0.867 A**

Since the calculated minimum inductor current is greater than zero, the ideal converter is expected to operate in Continuous Conduction Mode (CCM) at the specified load.

## 6. Output Capacitor Ripple Voltage

For an ideal output capacitor, neglecting ESR and assuming triangular inductor ripple current, the approximate peak-to-peak output voltage ripple is:

ΔVout ≈ ΔIL / (8 × fs × C)

Substituting:

ΔVout = 0.265 / (8 × 50,000 × 220 × 10⁻⁶)

**ΔVout ≈ 0.00301 V**

Therefore:

**Ideal Capacitor Ripple Voltage ≈ 3.01 mV peak-to-peak**

This is an ideal estimate. Actual output ripple will also depend on capacitor ESR, ESL, switching behaviour and other parasitic effects.

## 7. Comparison with LTspice Simulation

The initial LTspice simulation included practical parasitic parameters in the circuit model.

The approximate simulation observations are:

| Parameter | Ideal Calculation | LTspice Observation |
|---|---:|---:|
| Output Voltage | 5 V | 4.7–4.8 V |
| Average Inductor Current | 1 A | Approximately 0.95 A |
| Load Current | 1 A | Approximately 0.95 A |
| Switching Frequency | 50 kHz | 50 kHz |
| Operating Mode | CCM expected | CCM observed |

The simulated load current is consistent with the output voltage and load resistance:

Iout = Vout / R

For an output voltage of 4.75 V:

Iout = 4.75 / 5

**Iout = 0.95 A**

The difference between the ideal calculations and simulation observations can be attributed to non-ideal circuit behaviour, including component parasitics and conduction losses.

The ideal ripple calculations should not be treated as measured LTspice ripple values. Those must be obtained directly from the simulated waveforms.

## 8. Observations and Further Investigation

The initial simulation demonstrates that the converter can step down the 12 V input towards the intended 5 V output.

However, further investigation is required in the following areas:

- Output voltage regulation and duty-cycle optimisation.
- Inductor current ripple under practical operating conditions.
- Output voltage ripple, including capacitor ESR and ESL effects.
- Startup transient response and output voltage overshoot.
- Switching losses and overall conversion efficiency.
- Influence of component parasitics on steady-state performance.

## 9. Conclusion

The theoretical calculations establish an ideal duty cycle of approximately 41.67%, a switching period of 20 µs, and an expected average output current of 1 A.

The calculated inductor ripple current is approximately 265 mA peak-to-peak, while the ideal capacitive output voltage ripple is approximately 3.01 mV peak-to-peak.

The LTspice simulation produces an output voltage of approximately 4.7–4.8 V, indicating that practical circuit losses and parasitic effects must be considered when optimising the converter.

These calculations provide a theoretical reference for further simulation analysis and design refinement.