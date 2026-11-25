# LTspice Simulation Analysis

## 1. Overview

This document records the quantitative results obtained from the LTspice transient simulation of the 12 V to 5 V DC-DC buck converter.

The measurements establish a baseline for evaluating output voltage regulation, inductor current ripple, output voltage ripple, startup response and operating mode.

The circuit parameters were kept unchanged during this analysis.

## 2. Simulation Configuration

| Parameter | Value |
|---|---|
| Input Voltage | 12 V |
| Target Output Voltage | 5 V |
| Switching Frequency | 50 kHz |
| Switching Period | 20 µs |
| Inductor | 220 µH |
| Output Capacitor | 220 µF |
| Load Resistance | 5 Ω |
| PMOS ON Time | 8.333 µs |
| Output Voltage Node | V(n003) |
| Inductor Current | I(L1) |
| Simulation Duration | 10 ms |

## 3. Steady-State Measurements

Average and RMS measurements were obtained over the 5 ms to 9 ms interval.

| Parameter | Measured Value |
|---|---:|
| Average Output Voltage | 4.6431 V |
| RMS Output Voltage | 4.6431 V |
| Average Inductor Current | 0.9279 A |
| RMS Inductor Current | 0.9311 A |

The average output voltage is approximately 7.14% below the 5 V target.

The average inductor current is consistent with the load current calculated using Ohm's law:

Iout = Vout / R

Iout = 4.6431 / 5

Iout ≈ 0.9286 A

## 4. Inductor Current Analysis

Measurements were obtained over the 7.00 ms to 7.10 ms interval.

| Parameter | Measured Value |
|---|---:|
| Maximum Inductor Current | 1.0816 A |
| Minimum Inductor Current | 0.7371 A |
| Peak-to-Peak Ripple Current | 0.3445 A |
| Average Inductor Current (5–9 ms) | 0.9279 A |

The minimum steady-state inductor current remains above zero.

Therefore, the converter operates in Continuous Conduction Mode (CCM) under the simulated steady-state conditions.

The measured current ripple is higher than the initial ideal theoretical estimate and requires further investigation.

## 5. Output Voltage Ripple

Measurements were obtained over the same 7.00 ms to 7.10 ms interval.

| Parameter | Measured Value |
|---|---:|
| Maximum Output Voltage | 4.6482 V |
| Minimum Output Voltage | 4.6338 V |
| Peak-to-Peak Output Ripple | 14.39 mV |

The output voltage remains relatively stable during steady-state operation.

The measured ripple includes the effects of capacitance, ESR, ESL and other circuit parasitics.

## 6. Startup Transient Analysis

Startup measurements were obtained over the 0 ms to 2 ms interval.

| Parameter | Measured Value |
|---|---:|
| Peak Output Voltage | 6.8568 V |
| Peak Inductor Current | 4.3449 A |
| Steady-State Output Voltage | 4.6431 V |

The output voltage exhibits significant startup overshoot before settling towards its steady-state value.

The peak voltage represents approximately 47.7% overshoot relative to the steady-state output voltage.

The initial inductor current surge is associated with charging the output filter and the transient response of the converter.

Further investigation is required to understand and reduce the startup overshoot and current surge.

## 7. Summary of Simulation Results

| Parameter | Simulation Result |
|---|---:|
| Output Voltage | 4.6431 V |
| Inductor Current Average | 0.9279 A |
| Inductor Current Ripple | 344.5 mA |
| Output Voltage Ripple | 14.39 mV |
| Startup Voltage Overshoot | 6.8568 V |
| Startup Peak Inductor Current | 4.3449 A |
| Operating Mode | CCM |

## 8. Areas for Further Investigation

The following aspects will be investigated during the optimisation stage:

1. Improving output voltage regulation towards 5 V.
2. Investigating the difference between theoretical and simulated inductor current ripple.
3. Reducing startup output voltage overshoot.
4. Reducing the initial inductor current surge.
5. Evaluating the influence of component parasitics.
6. Investigating switching losses and converter efficiency.
7. Exploring closed-loop output voltage regulation.

## 9. Conclusion

The LTspice simulation establishes a baseline for the performance of the 12 V to 5 V buck converter.

The converter achieves an average output voltage of 4.6431 V and operates in Continuous Conduction Mode under steady-state conditions.

However, the measured output voltage deviation, inductor current ripple and startup overshoot indicate opportunities for further optimisation.

These measurements will serve as reference values for subsequent design modifications.