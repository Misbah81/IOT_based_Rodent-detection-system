#  IOT-Based Intelligent Rodent Monitoring and Chemical Diffusion System for Critical Infrastructure

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: ESP32](https://img.shields.io/badge/Platform-ESP32-blue)](https://www.espressif.com/en/products/socs/esp32)
[![Protocol: MQTT](https://img.shields.io/badge/Protocol-MQTT-orange)](https://mqtt.org/)
[![Database: Firebase](https://img.shields.io/badge/Database-Firebase-red)](https://firebase.google.com/)

A complete IoT solution for automated rodent detection and chemical repellent deployment in critical infrastructure using ESP32, MQTT with CBOR encoding, Firebase Firestore, and real-time web dashboard.

---

## 📑 Table of Contents

- [About](#-about)
- [Introduction](#-introduction)
- [Hardware Requirements](#-hardware-requirements)
- [Software Requirements](#-software-requirements)
- [GitHub Repository](#-github-repository)
- [Installation Steps](#-installation-steps)
- [Project Structure](#-project-structure)
- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Usage](#-usage)
- [Screenshots](#-screenshots)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## 🔍 About

This project solves the critical problem of **rodent infestation in data centers, server rooms, and industrial facilities** where rats cause millions of dollars in damage by chewing through cables and creating downtime.

**Key Innovation:** Instead of traditional traps or liquid sprays (which can damage electronics), we use **non-conductive chemical fumes** via ultrasonic humidifiers, controlled by an intelligent IoT system.

---

## 📖 Introduction

### Problem Statement
- Rats damage networking cables, fiber optics, and power lines
- Traditional pest control methods are unsafe for sensitive electronics
- No real-time monitoring or automated response systems

### Our Solution
✅ **Ultrasonic motion detection** (instead of PIR)  
✅ **Automatic chemical diffusion** via humidifier  
✅ **Gas concentration monitoring** for safety  
✅ **Real-time cloud monitoring** via Firebase  
✅ **Remote control** via web dashboard  
✅ **Industry-standard protocols** (MQTT + CBOR)  
✅ **Scheduled automation** (4 sprays daily) + motion-triggered response  

### Why This Project?
- Combines **IoT, Cloud Computing, Embedded Systems, and Web Development**
- Demonstrates **industry-standard architecture** (Edge-Cloud pattern)
- Solves a **real engineering problem** with commercial potential
- Perfect for **data centers, telecom rooms, and industrial facilities**

---

## 🔧 Hardware Requirements

| Component | Quantity | Specification | Purpose |
|-----------|----------|---------------|---------|
| **ESP32 DevKit V1** | 1 | Dual-core 240MHz, WiFi + Bluetooth | Main microcontroller |
| **HC-SR04 Ultrasonic Sensors** | 2 | Range: 2cm - 400cm | Motion detection |
| **MQ-135 Gas Sensor** | 1 | Detects NH3, NOx, CO2 | Monitor chemical fume levels |
| **5V Relay Module** | 1 | 10A, Active LOW | Control humidifier |
| **Ultrasonic Humidifier** | 1 | 5V, USB-powered | Disperse chemical repellent |
| **Breadboard** | 1 | 830 tie points | Prototyping |
| **Jumper Wires** | - | Male-Male, Male-Female | Connections |
| **Power Supply** | 1 | 5V 2A USB adapter | Power ESP32 and humidifier |

**Total Estimated Cost:** ~$25-30 USD

---

## 💻 Software Requirements

### Development Environment
- **Arduino IDE** (v2.0+) - For ESP32 firmware
- **Python 3.8+** - For Flask backend
- **VS Code** (Recommended) - For web development

### Libraries & Frameworks

**ESP32 Firmware:**
```cpp
- PubSubClient (MQTT)
- TinyCBOR (Binary encoding)
- WiFi.h
- NTP Client (Time sync)
