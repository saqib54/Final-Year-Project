<!-- Banner -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:4CAF50,100:2196F3&height=200&section=header&text=Welcome%20to%20My%20GitHub!&fontSize=40&fontColor=ffffff" alt="header"/>


<p align="center">
  <b>Brain-Controlled Prosthetic Arm (Non-Invasive BCI)</b><br>
  Assistive Neurotechnology • Embedded Systems • Human-Machine Interaction
</p>

<p align="center">
  Developed with ❤️ for Accessible Healthcare Innovation
</p>

<p align="center">
  <img src="https://img.shields.io/badge/BCI-Enabled-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/ESP32-Powered-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/EEG-Controlled-success?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Non--Invasive-Tech-important?style=for-the-badge" />
</p>

---


---

# Brain-Controlled Prosthetic Arm (BCI)

This project presents a non-invasive **Brain-Computer Interface (BCI)** system designed to restore mobility for individuals with upper-limb impairments. It translates neural intent (EEG signals) into mechanical actions (Prosthetic Arm movements) using real-time signal processing and embedded intelligence.

---

## 📋 Project Objective

To develop a low-cost, high-accuracy assistive device that:

1. Captures raw brainwaves using a single-channel EEG headset.
2. Filters out **gratuitous frequencies** and artifacts (noise).
3. Interprets user intent (Blinks/Attention) to control a **3D-designed prosthetic arm**.
4. Provides a safe, non-invasive alternative to surgical implants.

---

## 🏗 System Architecture (Design Logic)

The system follows a modular pipeline from signal acquisition to mechanical actuation.

```mermaid
graph LR
    subgraph "Signal Acquisition"
    A[Human Brain] -->|Neural Waves| B[Dry Electrodes]
    B --> C[TGAM Module]
    end

    subgraph "Processing Unit"
    C -->|Filtered Data| D[ESP32 Microcontroller]
    D -->|Feature Extraction| E{Decision Logic}
    end

    subgraph "Actuation"
    E -->|Open Command| F[Robotic Hand]
    E -->|Close Command| F
    end

    style C fill:#f96,stroke:#333
    style D fill:#69f,stroke:#333
    style F fill:#9f9,stroke:#333

```

---

## 🛠 Hardware Specifications

### **Primary Components**

* **Sensor Unit:** **TGAM (ThinkGear AM)** Module with integrated ASIC for hardware-level filtering.
* **Processing Unit:** **ESP32** (32-bit Dual Core) – chosen for its high-speed clock and built-in Bluetooth/WiFi capabilities.
* **Electrodes:** Non-invasive Dry Electrodes (Forehead placement at Fp1).
* **Power:** 9V Lithium-Ion Battery with a voltage regulator for stable 3.3V/5V rails.

### **Mechanical Design**

* **Structure:** 3D Printed Prosthetic Hand (PLA/ABS).
* **Actuators:** High-torque Servo Motors (for finger flexion and extension).
* **Transmission:** Bio-inspired tendon-wire system.

---

## 🧪 Development & Troubleshooting (Engineering Logs)

The project evolved through iterative testing of different hardware configurations:

| Phase | Setup | Result | Observation |
| --- | --- | --- | --- |
| **01** | Arduino + ADS1256 | **FAILED** | The 8-bit Arduino processor was not capable of real-time sampling and complex math for EEG. |
| **02** | ESP32 + ADS1256 | **FAILED** | High **gratuitous frequency** (50Hz noise) and electrical interference masked the brain signals. |
| **03** | **ESP32 + TGAM** | **SUCCESS** | The TGAM’s built-in **Notch Filter** and Bandpass filters provided clean, stable data. |

---

## 💻 Software Workflow

The logic focuses on detecting **Attention Levels** and **Eye Blinks** to trigger the prosthetic hand.

```mermaid
sequenceDiagram
    participant User
    participant Headset
    participant ESP32
    participant RoboticArm

    User->>Headset: Imagines Movement (Motor Imagery)
    Headset->>Headset: Hardware Filtering (Notch + Bandpass)
    Headset->>ESP32: Serial Data Packet (512Hz)
    ESP32->>ESP32: Analyze Signal Strength & Attention
    alt Attention > Threshold
        ESP32->>RoboticArm: Move Command (Close Hand)
    else Double Blink Detected
        ESP32->>RoboticArm: Move Command (Open Hand)
    end
    RoboticArm-->>User: Visual Feedback

```

---

## 📐 3D Design & Modeling

The arm structure was designed in CAD to mimic natural human anatomy.

* **Degrees of Freedom (DOF):** 5-DOF (Individual finger movement).
* **Material:** Optimized for 3D printing with reinforced joints to prevent mechanical wear.
* **Simulation:** Tested in a virtual environment for workspace restrictions before physical prototyping [15].

---

## 👥 Project Credits

### **Development Team**

* **Saqib Azair** – Lead Hardware Developer & System Integration.
* **Hiba Zari Nadeem** – Research Lead & Documentation.
* **Shahbano** – 3D Modeling & CAD Design.

### **Supervision**

* **Supervisor:** Mr. Syed Waleed Hussain
* **Co-Supervisor:** Dr. Umair Muneer Butt
* **Department:** Computer Science, **UMT Sialkot**.

---

## 📚 Core References (APA)

1. **Zaim, A., et al. (2025).** *Iterative learning networks for brain-signal calibration*. Journal of Rehabilitation Robotics.
2. **Chen, X., & Wang, Y. (2025).** *Deep learning for synchronizing human thoughts with robotic systems*. Journal of Neural Engineering.
3. **Torad, M., et al. (2024).** *Brain-controlled robotic arm system using EEG signal*. International Journal of Industry and Sustainable Development.
4. **Cutipa-Puma, D. R. (2023).** *A low-cost robotic hand prosthesis controlled by EEG signals*. HardwareX.

---
## 📸 System Preview

<p align="center">
  <img src="assets/images/system-demo.png" width="700"/>
</p>

---

## 🎥 Project Demonstration

<p align="center">
  <video src="assets/videos/demo.mp4" controls width="700"></video>
</p>
### **How to Deploy**

1. **Wire up:** Connect TGAM TX to ESP32 RX.
2. **Code:** Flash `ESP32_BCI_Logic.ino` using Arduino IDE.
3. **Calibrate:** Wear the headset and stay still for 10 seconds to establish the signal baseline.
4. **Action:** Focus on a single thought or blink twice to see the prosthetic arm move.
---


<p align="center">
  © 2026 Brain-Computer Interface Research Project<br>
  Department of Computer Science • UMT Sialkot
</p>
