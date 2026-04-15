# Smart Medicine Storage Monitoring System

ESP32 BLE Mesh + Anedya Cloud

---

## Overview

This project is a smart IoT-based medicine storage monitoring system using ESP32 and BLE Mesh. It ensures safe storage conditions by continuously monitoring temperature, humidity, and light, and automatically controlling cooling mechanisms.

---

## Features

* 🌡 Temperature & humidity monitoring (DHT22)
* 💡 Light detection using LDR
* 🔁 Automatic cooling using servo motor
* 📡 BLE Mesh communication between nodes
* ☁ Cloud integration using Anedya
* ⚡ Edge-based automation (works without internet)

---

## System Architecture

* **Node 1:** LDR + Relay (light detection)
* **Node 2:** DHT22 + Servo (temperature control)
* **Gateway:** ESP32 (BLE Mesh + WiFi + MQTT)

---

## Working Principle

1. Sensor nodes collect environmental data
2. Data is sent via BLE Mesh
3. Gateway uploads data to cloud
4. If temperature > 30°C → Servo activates
5. Cloud can also send control commands

---

##  Project Structure

* firmware/ → ESP32 code
* docs/ → project report
* images/ → setup images
* data/ → sample command payloads

---

## Future Improvements

* Mobile app integration
* Alert notifications
* Battery-powered nodes
* AI-based prediction

---

## Author

Devam Gor
