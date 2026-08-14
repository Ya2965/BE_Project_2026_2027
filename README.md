````markdown
# BE Capstone Project

## Project Title

**Design and Development of a NIR-Based Optical Sensing Prototype for Glucose Trend Correlation**

https://youtu.be/MuU9FWgoZak
---

## Team Details

| Sr. No. | Name of Student  | Roll No. | Branch                  | Email ID                                                                  |
| ------- | ---------------- | -------- | ----------------------- | ------------------------------------------------------------------------- |
| 1       | Swarali Desai    | 06       | Automation and Robotics | [2023.swarali.desai@ves.ac.in](mailto:2023.swarali.desai@ves.ac.in)       |
| 2       | Sushant Lokhande | 47       | Automation and Robotics | [2023.sushant.lokhande@ves.ac.in](mailto:2023.sushant.lokhande@ves.ac.in) |
| 3       | Vedika Date      | 35       | Automation and Robotics | [2023.vedika.date@ves.ac.in](mailto:2023.vedika.date@ves.ac.in)           |
| 4       | Yash Jadhav      | 39       | Automation and Robotics | [2023.yash.jadhav@ves.ac.in](mailto:2023.yash.jadhav@ves.ac.in)           |

---

## Guide Details

**Project Guide:** Kader Shaikh
**Department:** Automation and Robotics
**Institute:** VESIT, Mumbai

---

## Problem Statement

> There is a need for a non-invasive, painless, and convenient approach for monitoring blood glucose trends without repeated skin penetration. Existing glucometers commonly use invasive finger-prick methods, which can be painful and inconvenient for frequent monitoring and require recurring consumables such as strips and lancets. This project aims to investigate the feasibility of using NIR-based optical sensing to correlate tissue optical responses with blood glucose trends.

---

## Abstract

Diabetes requires regular blood glucose monitoring, while conventional finger-prick glucometers involve invasive measurements that can be inconvenient and uncomfortable for frequent use. This project proposes the design and development of a NIR-based optical sensing prototype for investigating blood glucose trend correlation without skin penetration. The proposed system uses two NIR wavelengths, 850 nm and 940 nm, which are switched to generate optical signals through a finger. A BPW34 photodiode captures the resulting optical response, which is amplified using a transimpedance amplifier based on MCP6002 or OPA380. The amplified signal is digitized using a 16-bit ADS1115 ADC and processed using an ESP32. Signal-processing techniques such as noise filtering, baseline drift correction, ambient-light cancellation, absorbance-ratio calculation, and multi-wavelength correlation will be investigated. The optical measurements will be compared with reference glucometer readings to study their relationship with blood glucose trends. The project also considers the possible application of pigmentation and temperature compensation algorithms. The expected outcome is a portable, low-cost optical sensing prototype for research into non-invasive glucose monitoring.

---

## Objectives

1. To study the existing problem and principles of NIR spectroscopy for glucose sensing.
2. To design a suitable optical sensing and signal acquisition architecture.
3. To generate NIR signals using 850 nm and 940 nm LEDs through wavelength switching.
4. To detect the optical response using a BPW34 photodiode.
5. To amplify the photodiode signal using a transimpedance amplifier.
6. To acquire the signal using a 16-bit ADS1115 ADC and ESP32.
7. To implement signal processing including noise filtering, baseline correction, and ambient-light cancellation.
8. To investigate absorbance-ratio and multi-wavelength features for glucose trend correlation.
9. To validate device readings against reference glucometer measurements.
10. To investigate the possible use of pigmentation and temperature compensation algorithms.

---

## Scope of the Project

* Design and development of a NIR-based optical sensing prototype
* Generation of optical signals using 850 nm and 940 nm NIR LEDs
* Finger-based optical measurement
* BPW34 photodiode-based detection
* Transimpedance amplification using MCP6002 / OPA380
* 16-bit ADC-based signal acquisition using ADS1115
* ESP32-based data acquisition and processing
* Noise filtering and baseline drift correction
* Ambient-light cancellation
* Absorbance-ratio calculation
* Multi-wavelength correlation
* Data collection and validation against a standard glucometer
* Investigation of pigmentation and temperature compensation
* Performance analysis of the prototype

---

## Existing System

Currently available glucometers commonly use invasive finger-prick methods for blood glucose measurement. The user must obtain a blood sample and use a disposable test strip to determine the glucose level.

Limitations include:

* Invasive finger-prick measurement
* Pain and discomfort during frequent testing
* Recurring cost of strips and lancets
* Inconvenience for frequent monitoring
* Risk of infection
* Reduced patient compliance over time

Existing wearable devices can provide vital-parameter monitoring, but reliable non-invasive glucose sensing remains a challenge.

---

## Proposed System

The proposed system is a spectroscopy-based optical sensing prototype that uses the absorption and reflection properties of human tissue to investigate blood glucose trends without skin penetration.

The system will use:

* **NIR LEDs:** 850 nm and 940 nm
* **Photodiode:** BPW34
* **Transimpedance Amplifier:** MCP6002 / OPA380
* **ADC:** ADS1115, 16-bit
* **Microcontroller:** ESP32
* **Optional:** OLED display, temperature sensor, and pressure sensor
* **Finger-clip enclosure**

The two NIR wavelengths will be switched and transmitted through the finger. The BPW34 photodiode will detect the optical response, which will be amplified by the TIA and converted into digital data using the 16-bit ADC. The ESP32 will acquire and process the signal.

The processing will include noise filtering, baseline drift correction, ambient-light cancellation, absorbance-ratio calculation, and multi-wavelength correlation. The resulting measurements will be compared with standard glucometer readings to investigate glucose trends.

---

## System Architecture

Add block diagram or system architecture image here.

```markdown
![System Architecture](images/system_architecture.png)
```

The basic signal flow is:

```text
NIR LEDs
(850 nm & 940 nm)
        ↓
Finger
        ↓
Photodiode
(BPW34)
        ↓
TIA
(MCP6002 / OPA380)
        ↓
ADC
(16-bit ADS1115)
        ↓
ESP32
        ↓
Serial Monitor
```

The system architecture follows the proposed flow of generating two NIR signals, transmitting them through the finger, detecting the optical response, amplifying it, converting it using a 16-bit ADC, and processing the acquired data through the ESP32.

Briefly explain the architecture.

---

## Hardware Requirements

| Sr. No. | Component | Specification | Quantity | Purpose |
| ------- | --------- | ------------- | -------- | ------- |
| 1       |           |               |          |         |
| 2       |           |               |          |         |
| 3       |           |               |          |         |
| 4       |           |               |          |         |

---

## Software Requirements

| Sr. No. | Software / Tool | Version | Purpose |
| ------- | --------------- | ------- | ------- |
| 1       |                 |         |         |
| 2       |                 |         |         |
| 3       |                 |         |         |

---

## Technologies Used

Mention technologies used in the project.

Example:

* Embedded C / Python / JavaScript
* Arduino / STM32 / ESP32 / Raspberry Pi
* ROS / MATLAB / Simulink
* Machine Learning / Computer Vision
* IoT / Cloud / Mobile App
* PCB Design / CAD Design

---

## Methodology

Explain the step-by-step approach.

1. Literature survey
2. Problem identification
3. Requirement analysis
4. System design
5. Hardware/software development
6. Integration
7. Testing and validation
8. Documentation and publication

---

## Project Timeline

| Week / Month | Task Planned          | Status                            |
| ------------ | --------------------- | --------------------------------- |
| Week 1       | Problem finalization  | Pending / In Progress / Completed |
| Week 2       | Literature survey     |                                   |
| Week 3       | Requirement analysis  |                                   |
| Week 4       | System design         |                                   |
| Week 5       | Prototype development |                                   |
| Week 6       | Testing               |                                   |
| Week 7       | Documentation         |                                   |
| Week 8       | Paper writing         |                                   |

---

## Weekly Progress Updates

Students must update this section every week.

| Week   | Date | Work Completed | Work Planned for Next Week | Issues / Challenges | GitHub Commit Link |
| ------ | ---- | -------------- | -------------------------- | ------------------- | ------------------ |
| Week 1 |      |                |                            |                     |                    |
| Week 2 |      |                |                            |                     |                    |
| Week 3 |      |                |                            |                     |                    |
| Week 4 |      |                |                            |                     |                    |
| Week 5 |      |                |                            |                     |                    |
| Week 6 |      |                |                            |                     |                    |
| Week 7 |      |                |                            |                     |                    |
| Week 8 |      |                |                            |                     |                    |

---

## Design Files

Upload and link all design files here.

| File Type       | File Name / Link | Description |
| --------------- | ---------------- | ----------- |
| CAD Model       |                  |             |
| Circuit Diagram |                  |             |
| PCB Design      |                  |             |
| Flowchart       |                  |             |
| Simulation File |                  |             |

---

## Circuit Diagram

Add circuit diagram image here.

```markdown
![Circuit Diagram](images/circuit_diagram.png)
```

---

## Flowchart / Algorithm

Add flowchart image here.

```markdown
![Flowchart](images/flowchart.png)
```

### Algorithm

1. Start
2. Initialize the system
3. Read input from sensors/user
4. Process the data
5. Generate output/control action
6. Display/store/transmit result
7. Stop

---

## Implementation Details

Explain the actual implementation of the project.

### Hardware Implementation

Write details about connections, components, power supply, sensors, actuators, PCB, enclosure, etc.

### Software Implementation

Write details about code structure, libraries used, algorithms, communication protocols, database, app, cloud, etc.

---

## Code Structure

```text
BE-Capstone-Project/
│
├── README.md
├── docs/
│   ├── literature_survey.md
│   ├── project_report.pdf
│   └── presentation.pptx
│
├── hardware/
│   ├── circuit_diagram.png
│   ├── pcb_design/
│   └── cad_model/
│
├── software/
│   ├── src/
│   ├── include/
│   └── tests/
│
├── images/
│   ├── system_architecture.png
│   ├── prototype_photo.jpg
│   └── results.png
│
└── references/
    └── papers/
```

---

## How to Run the Project

### Step 1: Clone the Repository

```bash
git clone https://github.com/username/project-name.git
```

### Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

or mention specific software/library installation steps.

### Step 3: Upload / Run the Code

```bash
python main.py
```

or

```bash
arduino-cli upload -p COMx --fqbn board_name
```

### Step 4: Observe the Output

Mention the expected output of the project.

---

## Testing and Results

| Test No. | Test Description | Expected Result | Actual Result | Status      |
| -------- | ---------------- | --------------- | ------------- | ----------- |
| 1        |                  |                 |               | Pass / Fail |
| 2        |                  |                 |               | Pass / Fail |
| 3        |                  |                 |               | Pass / Fail |

---

## Result Images / Videos

Add images or videos of the working prototype.

```markdown
![Prototype](images/prototype_photo.jpg)
```

Video Link:

```markdown
[Project Demo Video](https://drive.google.com/your-video-link)
```

---

## Applications

Mention real-world applications of the project.

1.
2.
3.
4.

---

## Advantages

1.
2.
3.
4.

---

## Limitations

1.
2.
3.
4.

---

## Future Scope

Mention possible improvements.

1.
2.
3.
4.

---

## Research Paper / Publication

| Item                      | Details                                                   |
| ------------------------- | --------------------------------------------------------- |
| Paper Title               |                                                           |
| Conference / Journal Name |                                                           |
| Paper Status              | Not Started / Drafting / Submitted / Accepted / Published |
| Submission Date           |                                                           |
| Paper Link                |                                                           |

---

## References

Add references in IEEE format.

Example:

```text
[1] A. Author, B. Author, "Title of the Paper," Journal/Conference Name, vol. X, no. Y, pp. xx-yy, Year.
[2] Datasheet / Website / Book reference.
```

---

## Repository Update Guidelines

Each student team must update the GitHub repository regularly.

Minimum expected updates:

* Update README every week.
* Push code changes regularly.
* Upload circuit diagrams, CAD files, PCB files, reports and presentations.
* Add weekly progress in the progress table.
* Maintain proper folder structure.
* Do not upload unnecessary temporary files.
* Each major update should have a meaningful commit message.

Example commit messages:

```text
Added problem statement and objectives
Updated system architecture diagram
Added sensor interfacing code
Updated weekly progress for Week 3
Added testing results and prototype images
```

---

## Declaration

We declare that this project work is carried out by our team as part of the BE Capstone Project. The work will be regularly updated on GitHub and all references used will be properly cited.

---

## License

This project is for academic use only.

Optional:

```text
MIT License / Creative Commons / Institute Use Only
```

```
```
