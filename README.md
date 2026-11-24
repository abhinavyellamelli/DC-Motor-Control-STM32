# DC Motor Speed Control using STM32

Experimental characterization and **closed-loop speed control** of a 12 V DC geared motor on an **STM32 Nucleo-F446RE**, with the control model built in **MATLAB/Simulink** and deployed through code generation.

> Course project: **ED5211 – E-Mobility Lab 1**, IIT Madras (Jul–Nov 2026)

📄 **Full report:** [DC_Motor_Control_STM32_Report.pdf](DC_Motor_Control_STM32_Report.pdf)

---

## Overview

The project covers the full path from measuring a motor's parameters to controlling it in closed loop:

1. Measure the motor's electrical characteristics.
2. Build open-loop and closed-loop speed control on the STM32.
3. Reject supply-voltage disturbances with feedforward compensation.
4. Estimate speed without the encoder (sensorless estimation).

## Hardware

| Component | Purpose |
|---|---|
| 12 V, 170 RPM DC geared motor | With built-in Hall quadrature encoder |
| STM32 Nucleo-F446RE | PWM generation, sensing and control |
| L298N H-bridge | Bidirectional motor drive |
| Shunt + LM358P amplifier | Motor current sensing |
| Resistor divider | Supply voltage sensing |
| DSO, tachometer, multimeter | Measurements |

**Pin mapping:** PWM on TIM1_CH1 (PA8) · Encoder on TIM2 (PA0, PA1) · Direction on PC0, PC1 · Voltage on ADC1_IN4 (PA4) · Current on ADC2_IN8 (PB0)

## Key results

| Test | Result |
|---|---|
| Armature resistance (blocked rotor) | **25.59 Ω** |
| No-load speed vs voltage | N = 15.73 V − 8.83 RPM, **R² = 0.998** |
| PI controller gains | Kp = 0.45, Ki = 0.98 |
| Step response (0 → 100 RPM) | Rise time ≈ **1.5 s**, no visible overshoot, settling ≈ 3 s |
| Speed error under supply-voltage steps | **±13 RPM → ±3 RPM** with feedforward |
| Sensorless estimation | Speed estimated from measured motor voltage and current |

## Tools

`MATLAB` · `Simulink` · `STM32CubeMX` · `STM32 support package` · `Simulation Data Inspector`

## Repository contents

| File | Description |
|---|---|
| `DC_Motor_Control_STM32_Report.pdf` | Full lab report: characterization, models, results and task answers |
| `README.md` | This file |

## Team

- Yellamelli Abhinav (ED26M012)
- Robin Philip (ED26M009)
- Sogunuru Sivaramakrishna Anirudh (ED26M010)
- Y V S Gnaneswara Reddy (ED26M011)

Department of Engineering Design, IIT Madras · Batch 3
