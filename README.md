# Smart Medicine Storage Monitoring System

Distributed IoT system using ESP32 BLE Mesh, MQTT, and edge computing for real-time monitoring and control of medicine storage conditions.

---

## Overview

This project implements a smart medicine storage system that continuously monitors environmental parameters such as temperature, humidity, and light. It uses a BLE Mesh network for local communication between nodes and a cloud backend for remote monitoring and control.

The system is designed to operate reliably even without internet connectivity through edge-based automation.

---

## Demo

Watch the working demonstration:
https://drive.google.com/file/d/1f_mQ5gFi0ASkOhQcSh9SohPEBXPu874n/view

---

## System Architecture


[Node 1: LDR + Relay]        [Node 2: DHT22 + Servo]
           │                           │
           └────── BLE Mesh ───────────┘
                         │
                [Gateway ESP32]
        (BLE Mesh Client + WiFi + MQTT)
                         │
               WiFi + MQTTS (TLS)
                         │
                 [Anedya Cloud]
        (Dashboard + Database + Commands)


Sensor Nodes → BLE Mesh → Gateway → MQTT → Cloud  
Cloud Commands → Gateway → BLE Mesh → Nodes

**Components:**

* **Node 1:** LDR + Relay (light detection and control)
* **Node 2:** DHT22 + Servo (temperature monitoring and cooling)
* **Gateway:** ESP32 (BLE Mesh client, WiFi connectivity, MQTT communication)
* **Cloud:** Anedya platform (dashboard, database, command interface)

---

## Working Principle

1. Sensor nodes collect environmental data
2. Data is transmitted through BLE Mesh
3. Gateway node aggregates and uploads data to the cloud via MQTT
4. Edge logic triggers actuator response (e.g., servo activates if temperature > 30°C)
5. Cloud platform can send control commands back to nodes

---

## Operational Scenarios

### 1. Normal Monitoring

* Sensors continuously measure temperature, humidity, and light
* Data is sent via BLE Mesh to the gateway
* Gateway uploads data to the cloud dashboard
* No actuator is triggered

---

### 2. Edge-Based Automatic Cooling

* If temperature exceeds 30°C
* Node 2 activates the servo motor automatically
* Cooling mechanism starts without cloud dependency
* Ensures reliability during network failure

---

### 3. Manual Override via Cloud (Remote Control)

* User sends command from mobile dashboard (e.g., Blynk or web app)
* Command reaches gateway via MQTT
* Gateway forwards command through BLE Mesh
* Actuator (servo/relay) executes command even if temperature is below threshold

---

### 4. Offline Operation

* BLE Mesh continues working without internet
* Edge logic still performs temperature-based automation
* System remains functional in disconnected environments

---

### 5. Light-Based Automation

* LDR detects ambient light levels
* Relay activates or deactivates based on threshold
* Can be used for lighting or alert indication

---

### 6. Remote Monitoring

* User can view real-time environmental data
* Dashboard reflects live system conditions
* Enables monitoring from any location

---

### 7. Fail-safe Behavior

* If cloud connection is lost:

  * Edge automation continues
  * Local system remains operational
* Ensures system robustness and reliability

---

## Features

* Temperature and humidity monitoring using DHT22
* Light detection using LDR
* Automatic cooling using servo motor
* BLE Mesh-based communication between nodes
* Secure cloud integration using MQTT over TLS
* Edge-based automation for offline functionality

---

## Engineering Design Decisions

* **BLE Mesh:** Enables scalable multi-node communication without central dependency
* **Edge Computing:** Reduces latency and ensures system works without internet
* **MQTTS (TLS):** Provides secure and efficient cloud communication
* **Gateway Architecture:** Separates sensing layer from cloud communication layer

---

## Project Structure

* `firmware/` – ESP32 source code
* `docs/` – documentation and reports
* `images/` – hardware setup and outputs
* `data/` – sample payloads and configurations

---

## Future Improvements

* Mobile application integration
* Alert system (SMS/Email notifications)
* Battery-powered sensor nodes
* Predictive analytics using machine learning

---

## Author

Devam Gor




