# AUV-Hardware-Architecture
Jetson Orin Nano Super and Pixhawk4 based autonomus underwater vehicle (AUV) electronic power delivery and sensor schematics

# AUV Hardware & Power Architecture 🚀🤖

This repository contains the hardware architecture, power distribution system, and sensor integration schematics for our Autonomous Underwater Vehicle (AUV) project designed for the Teknofest competition.

As the Electronic Design and Power Systems Lead, my focus is on ensuring safe, efficient, and stable power delivery to all critical components while maintaining robust sensor communication.

## ⚡ Core System Components
* **AI & Vision Processing:** Jetson Orin Nano Super
* **Dive/Motion Controller:** Pixhawk 4
* **Power Source:** 16.000 mAh High-Capacity Battery
* **Safety & Switching:** ELO Contactor (Main Power Cut-off & Protection)
* **Acoustic Sensors:** Hydrophone Integration

## 🔋 Power Distribution Strategy
*### ⚡ AUV Power Distribution & Safety Architecture

Power system is designed for high reliability and strict hardware-level safety:

* **🔋 Main Battery & E-Stop:** Power originates from the main battery pack and routes through a **High-Current Contactor** controlled by an external **Emergency Stop (E-Stop)** switch. This ensures an instant, hardware-level power cut-off in case of emergencies.
* **🔀 Power Distribution Board (PDB):** Once the contactor is engaged, power flows into the central PDB, which efficiently splits the electrical network into two primary branches.
* **💪 High-Power Branch:** Routes raw, unregulated battery voltage directly to the ESCs and thrusters for maximum mechanical performance.
* **🧠 Logic Branch:** Routes power through DC-DC buck converters to provide a clean and stable 5V/12V supply to the main microcontrollers (Raspberry Pi / Pixhawk) and sensors.*

## 📂 Schematics & Diagrams
*(Schematics will be uploaded here soon.)*

---
*Note: Due to competition confidentiality guidelines, full proprietary schematics might be limited. The uploaded documents represent the general architecture and integration strategy.*
