#  IOT-Based Intelligent Rodent Monitoring and Chemical Diffusion System for Critical Infrastructure

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: ESP32](https://img.shields.io/badge/Platform-ESP32-blue)](https://www.espressif.com/en/products/socs/esp32)
[![Protocol: MQTT](https://img.shields.io/badge/Protocol-MQTT-orange)](https://mqtt.org/)
[![Database: Firebase](https://img.shields.io/badge/Database-Firebase-red)](https://firebase.google.com/)
[![Encoding: CBOR](https://img.shields.io/badge/Encoding-CBOR-purple)](https://cbor.io/)

A complete, industrial-grade IoT solution for automated rodent detection and safe chemical repellent deployment in data centers and critical infrastructure using ESP32, MQTT with CBOR encoding, Firebase Firestore, and a real-time web dashboard.

---

## 📑 Table of Contents

- [About](#-about)
- [Introduction](#-introduction)
- [Hardware Requirements](#-hardware-requirements)
- [Software & Technologies](#-software--technologies)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Installation & Setup](#-installation--setup)
- [Features](#-features)
---

## 🔍 About

This project solves the critical problem of **rodent infestation in data centers, server rooms, and industrial facilities** where rats cause millions of dollars in damage by chewing through cables and creating critical downtime.

**Key Innovation:** Instead of traditional traps or liquid sprays (which can cause short circuits in electronics), we use **non-conductive chemical fumes** via ultrasonic humidifiers, controlled by an intelligent, cloud-connected IoT system.

---

## 📖 Introduction

### Problem Statement
- Rats damage networking cables, fiber optics, and power lines.
- Traditional pest control methods (liquids/poisons) are unsafe for sensitive electronics.
- Lack of real-time monitoring and automated response systems in server rooms.

###  Solution
✅ **Ultrasonic motion detection** (highly precise, replaces PIR)  
✅ **Automatic chemical diffusion** via ultrasonic humidifier  
✅ **Gas concentration monitoring** (MQ-135) for human/equipment safety  
✅ **Real-time cloud monitoring** via Firebase Firestore  
✅ **Remote control** via responsive Web Dashboard  
✅ **Industry-standard protocols** (MQTT + CBOR for ultra-low latency)  
✅ **Scheduled automation** (4 sprays daily) + motion-triggered response  

---

## 🔧 Hardware Requirements

| Component | Quantity | Specification | Purpose |
|-----------|----------|---------------|---------|
| **ESP32 DevKit V1** | 1 | Dual-core 240MHz, WiFi + BT | Main microcontroller |
| **HC-SR04 Ultrasonic Sensors** | 2 | Range: 2cm - 400cm | Precision motion detection |
| **MQ-135 Gas Sensor** | 1 | Detects NH3, NOx, CO2 | Monitor chemical fume levels |
| **5V Relay Module** | 1 | 10A, Active LOW | Control humidifier power |
| **Ultrasonic Humidifier** | 1 | 5V, USB-powered | Disperse chemical repellent |
| **Breadboard & Jumper Wires** | 1 set | Standard | Prototyping connections |
| **Power Supply** | 1 | 5V 2A USB adapter | Power ESP32 and humidifier |

---

## 💻 Software & Technologies

| Layer | Technology | Purpose |
|-------|------------|---------|
| **Firmware** | Arduino IDE (C++) | ESP32 programming and hardware control |
| **Protocol** | MQTT (HiveMQ/EMQX) | Lightweight, real-time IoT communication |
| **Encoding** | CBOR (TinyCBOR library) | Binary data encoding (50% smaller payload than JSON) |
| **Backend** | Python 3.x + Flask | Secure middleware gateway and data processing |
| **Database** | Firebase Firestore | Cloud NoSQL database for real-time data storage |
| **Frontend** | HTML5 + Bootstrap 5 + Chart.js | Responsive web dashboard and live visualization |
| **Libraries (ESP32)** | PubSubClient, TinyCBOR, WiFi, NTP | Hardware communication & time synchronization |
| **Libraries (Python)** | paho-mqtt, cbor2, firebase-admin | Backend MQTT handling and cloud integration |

---

## 🏗️ System Architecture

The system follows a secure **Edge-to-Cloud Gateway Architecture** to ensure API keys remain secure and ESP32 processing load is minimized.
<img width="1536" height="1024" alt="2" src="https://github.com/user-attachments/assets/10ef1654-3ff1-4d9d-977b-8310affdef09" />


---

## ⚙️ Installation & Setup

### 1. ESP32 Firmware Setup
1. Open `esp32_code/esp32_rodent_system.ino` in **Arduino IDE**.
2. Install required libraries via Library Manager: `PubSubClient` and `TinyCBOR`.
3. Update WiFi credentials (`ssid` and `password`) in the code.
4. Select **ESP32 Dev Module** from the Board Manager and upload the code.

### 2. Backend Setup (Python)
```bash
cd backend

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Setup Firebase
# 1. Download firebase_service_account.json from Firebase Console
# 2. Place it inside the 'backend' folder

# Run the backend
python app.py
```

### 3. Web Dashboard Setup
1. Open `web_dashboard/index.html` in any modern web browser (or use VS Code Live Server).
2. **Important:** Update the `FIREBASE_CONFIG` object at the top of the `<script>` tag with your actual Firebase Web App credentials.
3. The dashboard will automatically connect to HiveMQ (via WebSockets) and Firebase.

---

## ✨ Features

### 🎯 Core Features
- **Real-time motion detection** using dual ultrasonic sensors with 3-sample noise filtering.
- **Automatic chemical diffusion** (15 seconds on motion detection).
- **Scheduled spraying** (4 times daily: 8 AM, 1 PM, 6 PM, 11 PM) via NTP time sync.
- **Gas concentration monitoring** with automatic safety cutoff (Hysteresis logic).
- **Remote manual control** via responsive web dashboard.

### 🔧 Technical Highlights
- **CBOR Encoding:** Payload size reduced by 50% compared to JSON, parsing is 10x faster.
- **Secure Edge-Cloud Architecture:** API keys are never exposed to the edge device (ESP32).
- **Moving Average Filter:** Smooths out MQ-135 gas sensor fluctuations.
- **Auto-Reconnect:** Robust MQTT connection handling for both ESP32 and Backend.

---
---

<div align="center">
  <sub>SOLUTION for IoT Innovation and Critical Infrastructure Safety</sub>
</div>
```


https://github.com/user-attachments/assets/ea8a831d-25a1-42b7-b2dd-bcea2b14b05b




