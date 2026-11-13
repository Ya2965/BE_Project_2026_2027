# Prototype 1 – Experimental Tests and Performance Evaluation

This directory documents the experimental tests performed on Prototype 1 of the NIR finger-sensing platform. The tests characterize the optical front end, evaluate measurement repeatability, and investigate factors that influence the measured NIR response.

The objective is to establish a stable and repeatable sensing setup before proceeding with larger glucose-paired data collection.

## 1. Experimental Setup

| Component | Configuration |
|---|---|
| Controller | ESP32 |
| NIR LEDs | 850 nm and 940 nm |
| Photodiode | BPW34 |
| Transimpedance Amplifier | MCP6002 (Amplifier A) |
| ADC | ADS1115, 16-bit |
| ADC Configuration | I2C address 0x48, A0, 128 SPS |
| I2C Pins | SDA – GPIO23, SCL – GPIO22 |
| LED Control | GPIO26 – 850 nm, GPIO25 – 940 nm |
| LED Resistor | 330 Ω |
| Reference Voltage | Approximately 1.65 V |
| Optical Enclosure | Black finger enclosure with fixed LED–photodiode geometry |
| LED Settling Time | 500 ms |

## 2. NIR Measurement Method

The measurement sequence used was:

1. Both LEDs OFF – record the initial baseline.
2. Switch ON the 850 nm LED and record the voltage.
3. Switch OFF the LEDs.
4. Switch ON the 940 nm LED and record the voltage.
5. Calculate the optical response for both wavelengths.

The response values were calculated as:

- **Δ850 = V_OFF1 − V_850**
- **Δ940 = V_OFF2 − V_940**

All response values are expressed in millivolts (mV).

## 3. Tests Performed

### 3.1 Same-Position Stability and Repeatability

Five consecutive measurement cycles were performed without changing finger position.

| Trial | Δ850 (mV) | Δ940 (mV) |
|---|---:|---:|
| 1 | 88.0 | 26.0 |
| 2 | 86.1 | 26.0 |
| 3 | 85.1 | 26.0 |
| 4 | 86.0 | 26.0 |
| 5 | 86.0 | 26.0 |
| **Mean** | **86.24** | **26.0** |

**Observation:** Good short-term repeatability was observed when the finger remained in the same position.

### 3.2 Finger Repositioning Test

The finger was removed and reinserted between measurement cycles to evaluate placement-related variation.

| Trial | Δ850 (mV) | Δ940 (mV) |
|---|---:|---:|
| 1 | 80.0 | 24.0 |
| 2 | 78.0 | 24.0 |
| 3 | 77.8 | 22.9 |
| 4 | 82.2 | 24.0 |
| 5 | 80.0 | 24.0 |
| **Mean** | **79.6** | **23.8** |

**Observation:** Normal finger removal and reinsertion introduced measurable variation in the optical response.

### 3.3 Finger Pressure Test

Measurements were taken under normal and applied-pressure conditions.

| Condition | Δ850 (mV) | Δ940 (mV) |
|---|---:|---:|
| No pressure, initial | 70.6 | 26.0 |
| Maximum pressure, initial | 69.9 | 26.0 |
| Trial 1 – No pressure | 70.0 | 24.0 |
| Trial 2 – Pressure | 71.1 | 24.0 |
| Trial 3 – No pressure | 74.9 | 26.0 |
| Trial 4 – Pressure | 69.4 | 24.0 |

**Observation:** The pressure effect appeared small under the tested enclosure and setup. However, it could not be completely separated from repositioning and physiological variation.

### 3.4 Ambient-Light Test

The OFF baseline was measured with the enclosure closed, exposed to normal room light, and closed again.

| Condition | OFF Baseline (V) |
|---|---:|
| Enclosure closed | 1.6400 |
| Normal room light / exposed | 1.6400 |
| Closed again | 1.6400 |

**Observation:** No measurable ambient-light contribution was observed at the displayed measurement resolution under the tested conditions.

### 3.5 LED Switching and Settling-Time Test

Different LED settling intervals were evaluated to determine a suitable measurement delay.

| Settling Time | Δ850 (mV) | Δ940 (mV) |
|---|---:|---:|
| 100 ms | 82.0 | 16.0 |
| 500 ms | 82.0 | 19.3 |
| 1000 ms | 82.0 | 19.6 |

**Observation:** A 100 ms delay appeared insufficient for the 940 nm response. The 500 ms and 1000 ms readings were nearly identical.

**Selected settling time: 500 ms.**

### 3.6 Physiological / Blood-Perfusion Observation

A separate experiment investigated the effect of deliberately altering finger blood-perfusion conditions. This was recorded as a physiological observation, not a normal repositioning test.

| Trial | Δ850 (mV) | Δ940 (mV) |
|---|---:|---:|
| 1 | 53.8 | 16.0 |
| 2 | 52.0 | 0.0 |
| 3 | 51.8 | 0.0 |
| 4 | 52.7 | 0.0 |
| 5 | 52.0 | 0.0 |

**Observation:** The NIR response changed substantially under the altered perfusion condition compared with the normal same-position reference of approximately 86 mV at 850 nm and 26 mV at 940 nm.

This demonstrates that physiological conditions can significantly influence optical measurements. Deliberate tight finger constriction should not be repeated.

### 3.7 Post-Meal Repositioning Test

Five measurements were recorded after eating using normal finger placement and without deliberate pressure.

| Trial | Δ850 (mV) | Δ940 (mV) |
|---|---:|---:|
| 1 | 95.4 | 34.0 |
| 2 | 89.7 | 30.0 |
| 3 | 86.0 | 30.0 |
| 4 | 89.6 | 30.0 |
| 5 | 101.5 | 32.0 |
| **Mean** | **92.44** | **31.20** |

**Observation:** The readings were higher than those from the earlier normal repositioning test. However, the corresponding reference glucose measurement and other physiological conditions were not recorded alongside this dataset. Therefore, the difference cannot be attributed to glucose.

## 4. Glucose-Paired Observations

Two valid glucose-paired measurements were retained in the experimental documentation.

| Participant | Reference Glucose (mg/dL) | Δ850 (mV) | Δ940 (mV) |
|---|---:|---:|---:|
| P1 | 94 | 82.1 | 28.2 |
| P2 | 99 | 144.9 | 38.3 |

Only two valid observations are currently available. This dataset is insufficient to establish a relationship between glucose concentration and NIR response.

## 5. Key Experimental Findings

- The optical front end produced measurable responses at both 850 nm and 940 nm.
- The OFF baseline remained stable at approximately 1.6400 V during the reported tests.
- Good short-term repeatability was observed when finger position was maintained.
- Finger repositioning introduced measurable variation.
- The tested pressure effect appeared relatively small.
- No measurable ambient-light contribution was observed under the tested conditions.
- A settling time of 500 ms was selected for subsequent measurements.
- Altered blood-perfusion conditions produced substantial changes in NIR response.
- The available glucose-paired observations are insufficient to establish glucose-related correlation.

## 6. Current Test Status

| Test / Parameter | Status |
|---|---|
| Optical geometry characterization | Completed |
| Same-position repeatability | Completed |
| Finger repositioning | Completed |
| Finger pressure | Completed |
| Ambient-light influence | Completed |
| LED settling-time evaluation | Completed |
| Physiological / perfusion observation | Completed |
| Glucose-paired data collection | In Progress |
| PPG integration | Pending |
| Temperature sensor integration | Pending |

## 7. Next Steps

1. Integrate PPG sensing to capture pulsatile blood-volume and perfusion-related information.
2. Integrate temperature sensing to capture additional physiological context.
3. Synchronize NIR, PPG, temperature, and reference glucose measurements.
4. Collect a larger dataset with repeated measurements across participants.
5. Extract NIR features such as Δ850, Δ940, and normalized or ratio-based features.
6. Investigate glucose-associated variations while accounting for physiological and measurement-related factors.
7. Consider statistical and machine-learning models after sufficient paired data has been collected.

## 8. Important Note

Prototype 1 is an experimental optical sensing platform. The tests documented here characterize sensor behaviour and identify potential sources of measurement variation. They do not establish clinical glucose measurement accuracy, and the prototype is not intended to replace conventional glucometers.
