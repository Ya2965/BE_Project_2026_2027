# Hardware

This directory contains the hardware design and implementation details of the NIR spectroscopy-based optical sensing prototype for glucose trend correlation.

## Prototype 1

The first prototype establishes the basic NIR optical sensing arrangement using:

- **850 nm and 940 nm NIR LEDs** – provide near-infrared illumination.
- **BPW34 Photodiode** – detects transmitted optical signals.
- **Transimpedance Amplifier (TIA)** – converts the photodiode current into a measurable voltage.
- **ADS1115 ADC** – digitizes the conditioned analog signal.
- **ESP32** – acquires sensor readings and handles data transmission.

## Prototype 2

The second prototype extends the sensing setup by incorporating additional physiological measurements:

- **850 nm and 940 nm NIR LEDs** – dual-wavelength optical sensing.
- **OPA381** – precision transimpedance amplification.
- **TMP117** – temperature measurement.
- **MAX30102** – PPG signal acquisition.
- **ESP32** – sensor data acquisition and communication.

## Hardware Design

The hardware development covers:

- Optical sensing arrangement and finger enclosure.
- Photodiode signal conditioning.
- Sensor interfacing and data acquisition.
- Integration of temperature and PPG measurements.
- Prototype-level testing and calibration.

## Notes

The prototypes are experimental research systems intended to investigate the correlation between NIR optical measurements and reference glucose readings. They are not intended for clinical diagnosis or as replacements for conventional glucometers.
