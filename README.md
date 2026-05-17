# AUV & Mini ROV Hardware Architecture 🚀🤖

**Mavi Pusula Autonomous Underwater Vehicle - Electronic Power Delivery & Sensor Schematics**

This repository contains the hardware architecture, power distribution system, and sensor integration schematics for our dual-vehicle system (Main AUV + Mini ROV) designed for the Teknofest competition.

As the Electronic Design and Power Systems Lead, my focus is on establishing a highly deterministic, fail-safe power architecture. This includes ensuring absolute isolation between logic and actuator rails, optimizing tether dynamics, and providing stable power delivery to all critical components during autonomous missions.

## ⚡ Core System Components

### 1. Main AUV (Autonomous Underwater Vehicle)
* **AI & Vision Processing:** Jetson Orin Nano (running ROS/OpenCV for autonomous navigation and pipeline tracking)
* **Flight/Motion Controller:** Pixhawk 4
* **Propulsion:** 6x Letna G-350 (350KV) Brushless Thrusters with 30A ESCs
* **Power Source:** 14.8V 4S 12.000mAh 40C Li-Po (Strategically placed to act as passive ballast for negative buoyancy)
* **Sensors:** Arducam 8MP Sony IMX219 (CSI), D300 Depth/Temp Sensor, External I2C Compass, AHT10 Temp/Humidity, Leak Detectors.
* **Power Distribution:** Degz Hi-Base PDB (120A)

### 2. Mini ROV (Pipeline Inspection Module)
* **Logic & Vision:** Raspberry Pi + PCA9685PW (PWM Driver) + MPU6050 (I2C Gyro/Accelerometer)
* **Propulsion:** 3x F2838/T60 style Mini Thrusters with 40A ESCs
* **Internal Power Source:** 14.8V 4S 2200mAh 40C Li-Po
* **Power Distribution:** Matek PDB (100A Continuous / 120A Peak)

---

## 🔋 Power Distribution & Safety Architecture

Our power system is designed strictly around high-reliability and hardware-level safety protocols:

### 🔀 The "Thin Tether" Strategy (Zero Power Drag)
Instead of routing high-current power from the Main AUV to the Mini ROV (which requires thick, rigid cables that hinder maneuverability), **the Mini ROV is powered by its own internal 2200mAh battery**. 
* **Result:** The tether between the vehicles is reduced to a microscopic, highly flexible Cat5e Ethernet cable solely for data transfer, dropping tether drag to near zero and maximizing agility inside narrow pipelines.

### 🛡️ Dual E-Stop & Fusing Systems
Both vehicles operate as independent power islands:
* **Main AUV:** Main battery pack routes through a High-Current Contactor controlled by an external magnetic Emergency Stop (E-Stop).
* **Mini ROV:** Features its own localized magnetic E-Stop and a precisely calculated 60A/70A blade fuse to protect the 120A Matek PDB and the 88A max-discharge battery from stall-current catastrophic failures.

### 🔌 Complete Logic/Actuator Isolation (Anti-Brownout)
To prevent the flight controller from resetting due to voltage sags (brownouts) caused by mechanical stalls:
* **Isolated Servo Deployment:** The servo mechanism responsible for deploying the Mini ROV is powered by a completely independent 5V UBEC connected directly to the main 14.8V line. It shares **no** power rails with the Pixhawk's VCC. Pixhawk only provides the PWM signal (via `MAIN_OUT_7`).

### 💡 Intelligent Dimming Circuitry
* **Anti-Glare System:** To prevent camera sensor blinding from metal surfaces during the pipeline tracking mission, the 12V 20W COB LEDs are controlled via an **IRLZ44N MOSFET** connected to the PCA9685/Pixhawk. This allows real-time PWM dimming based on the environment's reflective properties.

---

## 📂 Schematics & Diagrams

*(Updated dual-vehicle schematics will be uploaded here shortly).*

> **Note:** Due to competition confidentiality guidelines, full proprietary schematics might be limited. The uploaded documents and KiCad/Proteus outputs represent the general architecture, safety protocols, and integration strategy.

**Mehmet Mustafa Gürel** *Electrical and Electronics Engineering | İnönü University*
