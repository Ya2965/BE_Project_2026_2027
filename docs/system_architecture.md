# System Architecture

## System overview

The project is organized around optical sensing, analog signal conditioning, embedded acquisition, and offline data analysis.

## Prototype 1 signal path

```text
850 nm NIR LED ─┐
                ├── Finger / optical transmission path ── BPW34 photodiode
940 nm NIR LED ─┘                                      │
                                                      ▼
                                           MCP6002 TIA stage
                                                      │
                                                      ▼
                                               ADS1115 ADC
                                                      │ I²C
                                                      ▼
                                                    ESP32
                                                      │
                                                      ▼
                                             Measurement logging
```

The LEDs are controlled sequentially by the ESP32. The photodiode current is converted to a voltage by the transimpedance amplifier, and the ADS1115 digitizes the conditioned signal.

## Prototype 2 extension

```text
NIR optical channel ───────────────┐
TMP117 temperature measurement ────┼── ESP32 acquisition
MAX30102 PPG measurement ──────────┘          │
                                             ▼
                                  Timestamped sensor records
                                             │
                                             ▼
                                  Data processing and analysis
```

This is a functional-level representation. Exact wiring, bus allocation, sampling configuration, and firmware interfaces should be documented alongside the implementation when finalized.

## Data-analysis path

```text
Raw sensor readings
       │
       ▼
Data quality checks and synchronization
       │
       ▼
Preprocessing and segmentation
       │
       ▼
Feature extraction
       │
       ▼
Exploratory analysis / regression
       │
       ▼
Evaluation against reference glucose
```

## Design considerations

- Keep the optical geometry as consistent as practical.
- Record OFF baselines and wavelength-specific ON readings.
- Use a documented LED settling interval.
- Preserve trial and participant identifiers.
- Record relevant measurement conditions to help interpret variability.
- Do not interpret optical response changes as glucose changes without paired data and analysis.
