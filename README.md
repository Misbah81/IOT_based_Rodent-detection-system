#  IOT-Based Intelligent Rodent Monitoring and Chemical Diffusion System for Critical Infrastructure
# 🐀 IoT-Based Intelligent Rodent Monitoring and Chemical Diffusion System for Critical Infrastructure

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: ESP32](https://img.shields.io/badge/Platform-ESP32-blue)](https://www.espressif.com/en/products/socs/esp32)
[![Protocol: MQTT](https://img.shields.io/badge/Protocol-MQTT-orange)](https://mqtt.org/)
[![Database: Firebase](https://img.shields.io/badge/Database-Firebase-red)](https://firebase.google.com/)

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
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

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

### Our Solution
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

```text
┌─────────────────────────────────────────────────────────────┐
│                    EDGE LAYER (ESP32)                        │
│  ┌──────────  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │Ultrasonic│  │Ultrasonic│  │  MQ-135  │  │  Relay   │   │
│  │ Sensor 1 │  │ Sensor 2 │  │  Sensor  │  │Humidifier│   │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘   │
│       └─────────────┴─────────────┴─────────────┘           │
│                        ESP32 (CBOR Encode)                   │
└────────────────────────────┬────────────────────────────────┘
                             │ MQTT (CBOR Binary)
                             ▼
─────────────────────────────────────────────────────────────┐
│              COMMUNICATION LAYER (MQTT Broker)               │
│                    HiveMQ / EMQX Cloud                       │
────────────────────────────┬────────────────────────────────
                             │
                ┌────────────┴────────────┐
                │                         │
                ▼                         ▼
┌──────────────────────────┐   ┌──────────────────────────┐
│    BACKEND LAYER         │   │   APPLICATION LAYER      │
│   Flask Python Backend   │   │   Web Dashboard          │
│  (CBOR Decode + Auth)    │   │  (Bootstrap + Chart.js)  │
└──────────┬───────────────   └──────────┬───────────────┘
           │                              │
           ▼                              ▼
─────────────────────────────────────────────────────────────┐
│                  CLOUD STORAGE LAYER                        │
│                  Firebase Firestore                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │device_status │  │    alerts    │  │control_logs  │     │
│  └──────────────┘  └──────────────┘  └──────────────     │
└─────────────────────────────────────────────────────────────┘
