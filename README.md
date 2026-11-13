# BE Capstone Project

## Project Title

**Development of a NIR Spectroscopy-Based Optical Sensing Prototype for Glucose Trend Correlation**

[Project Demonstration](https://youtu.be/MuU9FWgoZak)

---

## Team Details

| Sr. No. | Name of Student | Roll No. | Branch | Email ID |
| --- | --- | ---: | --- | --- |
| 1 | Swarali Desai | 06 | Automation and Robotics | 2023.swarali.desai@ves.ac.in |
| 2 | Sushant Lokhande | 47 | Automation and Robotics | 2023.sushant.lokhande@ves.ac.in |
| 3 | Vedika Date | 35 | Automation and Robotics | 2023.vedika.date@ves.ac.in |
| 4 | Yash Jadhav | 39 | Automation and Robotics | 2023.yash.jadhav@ves.ac.in |

---

## Guide Details

- **Project Guide:** Kader Shaikh
- **Department:** Automation and Robotics
- **Institute:** VESIT, Mumbai

---

## Problem Statement

Conventional blood glucose monitoring commonly relies on finger-prick measurements. Repeated skin puncturing can cause discomfort and inconvenience, particularly for frequent monitoring. This project investigates the feasibility of using near-infrared (NIR) optical measurements to study the relationship between tissue optical responses and reference blood glucose readings, with the aim of exploring glucose trend correlation without repeated blood sampling.

---

## Abstract

This project focuses on the development and experimental evaluation of two NIR-based optical sensing prototype configurations for investigating non-invasive glucose trend correlation. The first prototype uses two near-infrared wavelengths, 850 nm and 940 nm, to obtain optical measurements through a finger. A BPW34 photodiode detects the transmitted optical response, which is conditioned and acquired for analysis. The second prototype extends the sensing configuration by incorporating skin-temperature measurements, photoplethysmography (PPG)-derived features, and contextual parameters.

The acquired measurements are associated with reference glucose readings obtained using a conventional glucometer. The resulting dataset is used to investigate the relationship between NIR measurements and glucose readings, and to compare models based on NIR inputs alone with multivariate models that include additional physiological and contextual information. The project is an experimental investigation; it does not claim clinical validation or replacement of conventional glucose measurement devices.

---

## Objectives

1. Study the principles and research challenges of NIR spectroscopy for glucose sensing.
2. Design and develop an optical sensing and signal-acquisition system.
3. Generate NIR optical signals using 850 nm and 940 nm LEDs.
4. Detect optical responses using a BPW34 photodiode.
5. Develop suitable signal-conditioning and data-acquisition circuitry.
6. Acquire and record optical measurements using an ESP32-based system.
7. Investigate signal preprocessing and feature extraction for NIR measurements.
8. Incorporate additional physiological and contextual parameters in the second prototype.
9. Compare NIR-only and multivariate regression approaches.
10. Evaluate the relationship between prototype measurements and reference glucometer readings.

---

## Scope of the Project

- Development of two NIR-based optical sensing prototype configurations.
- Dual-wavelength optical measurement using 850 nm and 940 nm LEDs.
- Finger-based optical transmission measurement.
- Photodiode-based optical detection and signal conditioning.
- ESP32-based sensor acquisition.
- Integration of skin-temperature and PPG measurements in the second prototype.
- Recording of contextual information, including BMI and time since the last meal.
- Collection of reference glucose readings using a conventional glucometer.
- Dataset preparation, signal analysis, regression modelling, and comparative evaluation.
- Experimental investigation of the contribution of additional physiological and contextual parameters.

---

## Existing System

Conventional glucometers generally measure blood glucose using a small blood sample obtained through a finger prick. The sample is applied to a disposable test strip and analysed by the device.

Common limitations of repeated finger-prick monitoring include:

- Repeated skin puncturing.
- Discomfort during frequent measurements.
- Recurring use of test strips and lancets.
- Inconvenience when frequent measurements are required.

Non-invasive glucose monitoring remains a challenging research area because optical measurements from biological tissue are affected by factors other than glucose, including tissue composition, temperature, blood perfusion, skin properties, and sensor positioning.

---

## Proposed System

The proposed system investigates NIR optical sensing as a method for studying glucose trend correlation. It consists of two prototype configurations.

**Prototype 1 – Dual-Wavelength NIR Sensing**

The first prototype uses 850 nm and 940 nm NIR LEDs arranged for transmission measurement through a finger. A BPW34 photodiode detects the optical response. The detector signal is conditioned, digitised, and acquired by an ESP32-based system. This configuration establishes the baseline optical measurement setup.

**Prototype 2 – Multivariate Sensing**

The second prototype extends the first configuration by incorporating additional physiological measurements. It includes skin-temperature sensing using a TMP117 sensor and PPG acquisition using a MAX30102 sensor. The additional measurements, together with contextual information such as BMI and time since the last meal, are considered during data analysis.

Both configurations are compared against reference glucose readings obtained using a conventional glucometer. The comparison is intended to determine whether additional physiological and contextual inputs provide useful information beyond the NIR measurements alone.

---

## System Architecture

The overall system consists of an optical sensing stage, signal-conditioning and acquisition electronics, physiological sensors in the second prototype, and a data-analysis stage.

```text
                 PROTOTYPE 1
              Dual-Wavelength NIR
                       |
          850 nm and 940 nm LEDs
                       |
                 Finger
                       |
               BPW34 Photodiode
                       |
            Signal Conditioning
                       |
                 Data ADC
                       |
                    ESP32
                       |
              Acquired NIR Data
                       |
                       v
              Dataset and Analysis
                       ^
                       |
        Reference Glucose Measurements
             (Conventional Glucometer)


                 PROTOTYPE 2
              Multivariate Sensing
                       |
          NIR Optical Measurements
                       |
        +--------------+--------------+
        |                             |
   TMP117 Sensor                 MAX30102
 Skin Temperature                    PPG
        |                             |
        +--------------+--------------+
                       |
              Sensor Data Recording
                       |
          Contextual Information
          (BMI, Time Since Meal)
                       |
              Dataset and Analysis
                       |
          Multivariate Model Evaluation
```

The first prototype provides the NIR optical measurements used for baseline analysis. The second prototype adds temperature and PPG-derived information to investigate physiological compensation. Reference glucometer readings are recorded alongside the sensor measurements for model development and evaluation.

---

## Hardware Requirements

| Sr. No. | Component | Specification | Purpose |
| --- | --- | --- | --- |
| 1 | NIR LEDs | 850 nm and 940 nm | Optical illumination |
| 2 | Photodiode | BPW34 | Detection of optical response |
| 3 | Signal-conditioning circuit | Transimpedance amplifier | Photodiode signal conditioning |
| 4 | ADC | ADS1115, 16-bit | Digitisation of analogue measurements |
| 5 | Microcontroller | ESP32 | Sensor acquisition and data handling |
| 6 | Temperature sensor | TMP117 | Skin-temperature measurement in Prototype 2 |
| 7 | PPG sensor | MAX30102 | PPG acquisition in Prototype 2 |
| 8 | Reference instrument | Conventional glucometer | Reference glucose measurements |

---

## Software Requirements

| Software / Tool | Purpose |
| --- | --- |
| Arduino IDE | ESP32 firmware development and uploading |
| Python | Dataset processing and machine-learning analysis |
| MATLAB | Numerical and signal analysis |

---

## Technologies Used

- Near-Infrared (NIR) optical sensing
- Embedded systems and ESP32-based data acquisition
- Analogue signal conditioning and ADC interfacing
- Photoplethysmography (PPG)
- Temperature sensing
- Digital signal processing
- Dataset preparation and multivariate regression
- Experimental performance evaluation

---

## Methodology

1. **Literature Study:** Review NIR spectroscopy, non-invasive glucose monitoring, optical measurement configurations, and physiological sources of measurement variation.
2. **Requirement Analysis:** Identify the sensing, acquisition, and analysis requirements for both prototype configurations.
3. **Prototype 1 Development:** Develop the dual-wavelength optical sensing arrangement using 850 nm and 940 nm LEDs and a BPW34 photodiode.
4. **Signal Acquisition:** Condition and digitise the photodiode response and acquire measurements through the ESP32.
5. **Prototype 2 Development:** Extend the sensing configuration with TMP117 skin-temperature measurement and MAX30102 PPG acquisition.
6. **Reference Data Collection:** Record conventional glucometer readings corresponding to the sensor measurement sessions.
7. **Dataset Preparation:** Organise optical, physiological, contextual, and reference measurements for analysis.
8. **Model Development:** Develop regression models using NIR measurements and compare them with models incorporating additional inputs.
9. **Evaluation:** Compare model performance using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and coefficient of determination (R²).

---

## Project Timeline

| Period | Work |
| --- | --- |
| Week 1 | Problem definition, project objectives, and initial literature study |
| Week 2 | Review of NIR spectroscopy, glucose-sensing research, and optical measurement methods |
| Week 3 | Selection of wavelengths, photodetector, signal-conditioning approach, and acquisition architecture |
| Week 4 | Prototype 1 circuit development and optical measurement arrangement |
| Week 5 | Prototype 1 hardware integration and ESP32-based signal acquisition |
| Week 6 | Development of the second sensing configuration with temperature and PPG sensors |
| Week 7 | Experimental data workflow, reference glucose recording, and dataset organisation |
| Week 8 | Signal analysis, regression-model planning, comparative evaluation framework, and project documentation |

---

## Weekly Progress Updates

| Week | Work Completed |
| --- | --- |
| Week 1 | Finalised the project problem, aim, objectives, and scope. Initiated the study of non-invasive glucose monitoring and NIR spectroscopy. |
| Week 2 | Reviewed research on NIR glucose estimation, optical transmission and reflectance configurations, wavelength selection, and physiological measurement interference. |
| Week 3 | Finalised the two-wavelength sensing concept using 850 nm and 940 nm LEDs. Identified the BPW34 photodiode and the signal-acquisition requirements for Prototype 1. |
| Week 4 | Developed the first prototype circuit and optical arrangement. Worked on the photodiode signal-conditioning stage and finger measurement enclosure. |
| Week 5 | Integrated the optical sensing hardware with the ESP32-based acquisition setup and worked on obtaining the NIR sensor measurements. |
| Week 6 | Developed the second prototype configuration by extending the NIR setup with TMP117 temperature sensing and MAX30102 PPG acquisition. |
| Week 7 | Defined the experimental data workflow, including reference glucometer readings and recording of contextual parameters such as BMI and time since the last meal. |
| Week 8 | Organised the comparative analysis approach for NIR-only and multivariate regression models and consolidated the system design and experimental methodology. |

---

## Implementation Details

### Prototype 1: NIR Optical Sensing

Prototype 1 uses 850 nm and 940 nm NIR LEDs to illuminate a finger in a transmission-based arrangement. The BPW34 photodiode detects the optical response after it passes through the finger. The photodiode output is conditioned using a transimpedance amplifier and digitised using an ADS1115 16-bit ADC. The ESP32 is used for acquiring the digitised measurements.

The measurements from the two wavelengths form the baseline optical dataset for studying the relationship between NIR response and reference glucose readings.

### Prototype 2: Multivariate Sensing

Prototype 2 extends the optical measurement configuration with additional physiological sensing. A TMP117 sensor is used to obtain skin-temperature measurements, while a MAX30102 sensor is used to acquire PPG signals. Contextual parameters, including BMI and time since the last meal, are also considered during dataset preparation and analysis.

The additional inputs are investigated to determine whether they help account for physiological and measurement-related variations in the optical readings.

### Data Processing and Model Evaluation

The collected sensor measurements are organised with their corresponding reference glucose readings. The analysis compares two modelling approaches:

- **NIR-only approach:** Uses the optical measurements from the 850 nm and 940 nm channels.
- **Multivariate approach:** Uses NIR measurements along with additional physiological and contextual parameters.

Regression models are evaluated using MAE, RMSE, and R². The contribution of additional inputs is determined from experimental results rather than assumed in advance.

---

## Testing and Results

| Stage | Status |
| --- | --- |
| Hardware and sensor integration | Done |
|Initial Testing | Done|
| Data collection | In Progress |
| Data preprocessing and analysis | In Progress |
| Feature extraction and dataset preparation | In Progress |
| Regression model development | In Progress |
| Model evaluation and comparative analysis | In Progress |
| Final validation and performance assessment | In Progress |

---

## Applications

1. Experimental research into NIR-based non-invasive glucose monitoring.
2. Investigation of optical and physiological parameters for glucose trend correlation.
3. Comparative study of single-modality and multivariate sensor-based regression.
4. Development of compact optical sensing prototypes for biomedical instrumentation research.

---

## Advantages

1. Uses optical measurements without requiring blood extraction for the prototype's sensing process.
2. Uses two NIR wavelengths to obtain more than one optical measurement.
3. The second prototype incorporates temperature and PPG measurements for multivariate analysis.
4. Provides a platform for comparing NIR-only and enhanced sensor-input models.

---

## Limitations

1. Optical measurements are affected by tissue composition, skin properties, temperature, blood perfusion, and sensor positioning.
2. The first prototype uses only two NIR wavelengths, providing limited spectral information.
3. Model performance depends on the size, quality, and diversity of the collected dataset.
4. Experimental results do not establish clinical validity or suitability for medical decision-making.
5. Performance on the collected dataset may not generalise to unseen individuals or different measurement conditions.

---

## Future Scope

1. Expand the experimental dataset across a broader range of participants and measurement conditions.
2. Investigate additional optical wavelengths and sensing configurations.
3. Improve signal preprocessing and compensation for physiological and environmental variations.
4. Evaluate additional regression and machine-learning methods using consistent validation procedures.
5. Conduct further validation to assess generalisation across individuals and measurement sessions.

---

## Research Paper / Publication

The project includes a comparative experimental investigation of two NIR-based sensing configurations: a baseline dual-wavelength prototype and an extended multivariate prototype. The central research question is whether incorporating additional physiological and contextual parameters improves glucose trend correlation compared with using NIR measurements alone.

---

## Declaration

This project is carried out by the listed team as part of the BE Capstone Project under the Department of Automation and Robotics, VESIT, Mumbai. The work investigates NIR-based optical sensing for glucose trend correlation and is intended for academic and experimental research.

---

## License

This project is intended for academic and research purposes.
