# 💧 PCB-Based Real-Time Water Quality Monitoring Using Cloud Analytics

A compact, PCB-based IoT system that continuously monitors water quality parameters in real time and uploads data to the ThingSpeak cloud for live visualization and analysis.

---

## 📄 Abstract

This project designs and implements a PCB-based real-time water quality monitoring system targeting small-scale packaged drinking water industries. The system uses an **ESP32 microcontroller** to read data from **TDS**, and **Turbidity** sensors, calculates a **Water Quality Index (WQI)**, and transmits results to the **ThingSpeak cloud** via Wi-Fi. A **multi-level alarm system** (warning, critical, shutdown) triggers visual alerts and automatically isolates the water output using a **solenoid valve** during severe contamination events.

**Keywords:** IoT, Water Quality Monitoring, ESP32, ThingSpeak, PCB Design, TDS, Turbidity, Cloud Analytics

---

## ✨ Features

- Real-time monitoring of TDS, and Turbidity
- Water Quality Index (WQI) calculation from combined sensor data
- Multi-level alarm system — Warning, Critical, and Shutdown levels
- Automatic solenoid valve control during contamination events
- Live data visualization via ThingSpeak cloud (graphs, trends, values)
- Compact custom PCB for stable sensor interfacing and signal processing
- Wi-Fi connectivity using ESP32 — no extra communication module needed

---

## 🎯 Objective

To design and implement a PCB-based real-time water quality monitoring and multi-level alarm system that:

- Measures TDS, Turbidity, and Temperature continuously
- Provides a compact and reliable PCB for sensor signal processing
- Implements multi-level alarms for abnormal water conditions
- Automatically isolates water output via solenoid valve on severe contamination
- Uploads all data to the cloud for remote monitoring and analytics

---

## ⚠️ Problem Statement

Small-scale packaged drinking water industries lack an affordable, compact, and real-time embedded system to continuously monitor critical water quality parameters. The absence of automatic alerts and control mechanisms leads to delayed response, unsafe water packaging, production losses, and potential health risks to consumers.

---

## 🛒 Components Required

| Component | Role |
|---|---|
| ESP32 Microcontroller | Main MCU — reads sensors, processes data, sends to cloud via Wi-Fi |
| TDS Sensor | Measures Total Dissolved Solids (ppm) |
| Turbidity Sensor | Measures water clarity / suspended particles |
| Temperature Sensor | Measures water temperature |
| Solenoid Valve | Automatically shuts off water output on critical contamination |
| Custom PCB | Stable sensor interfacing and compact signal processing |
| Power Supply | Powers ESP32 and all sensors |

---

## 🏗️ System Architecture

```
┌────────────────────────────────────────────────┐
│               SENSING LAYER                    │
│     |     TDS Sensor + Turbidity Sensor     │
│                  
└──────────────────┬─────────────────────────────┘
                   │ Analog signals → ADC pins
┌──────────────────▼─────────────────────────────┐
│             PROCESSING LAYER                   │
│     ESP32 Microcontroller (Custom PCB)         │
│   ADC read → Data conversion → WQI calc        │
└────────┬───────────────────────┬───────────────┘
         │ Wi-Fi                 │ GPIO
┌────────▼──────────┐  ┌─────────▼──────────────┐
│   CLOUD LAYER     │  │    CONTROL LAYER        │
│  ThingSpeak       │  │  Multi-level Alarms     │
│  Graphs & Trends  │  │  Solenoid Valve Control │
│  Real-time Values │  │  Warning / Critical /   │
└───────────────────┘  │  Shutdown               │
                       └────────────────────────┘
```

---

## ⚙️ Working Principle

1. **Water Sample Interaction** — Sensors are placed directly in the water source
2. **Sensor Measurement** — pH, TDS, and Turbidity sensors produce analog signals
3. **Signal Processing** — ESP32 reads analog values via ADC pins
4. **Data Conversion** — Raw signals converted to TDS (ppm), and Turbidity level
5. **WQI Calculation** — All parameters combined into a single Water Quality Index score
6. **Alarm Evaluation** — System checks values against Warning / Critical / Shutdown thresholds
7. **Valve Control** — Solenoid valve automatically closes on shutdown-level contamination
8. **Wi-Fi Communication** — ESP32 sends all data to ThingSpeak cloud
9. **Cloud Visualization** — Data displayed as real-time graphs, values, and trends

---

## 📊 Alarm Levels

| Level | Condition | Action |
|---|---|---|
| Normal | All parameters within range | No action |
| Warning | One parameter slightly out of range | Visual alert triggered |
| Critical | Multiple parameters abnormal | Alarm activated |
| Shutdown | Severe contamination detected | Solenoid valve closes automatically |

---

## 💻 Code Upload Steps

1. Download and install [Arduino IDE](https://www.arduino.cc/en/software)
2. Add ESP32 board support via Board Manager
3. Install libraries: `ThingSpeak`, `WiFi`, `DHT`, `Wire`
4. Update Wi-Fi credentials in code:
   ```cpp
   const char* ssid = "YOUR_WIFI_SSID";
   const char* password = "YOUR_WIFI_PASSWORD";
   ```
5. Update ThingSpeak API key:
   ```cpp
   unsigned long myChannelNumber = CHANNEL_ID;
   const char* myWriteAPIKey = "YOUR_API_KEY";
   ```
6. Select **Tools → Board: ESP32 Dev Module**
7. Select correct **Tools → Port**
8. Click **Upload →**
9. Open **Serial Monitor** at 115200 baud to verify readings

---

## ☁️ ThingSpeak Cloud Setup

1. Create a free account at [thingspeak.com](https://thingspeak.com)
2. Create a new channel with fields: pH, TDS, Turbidity, Temperature, WQI
3. Copy your **Channel ID** and **Write API Key** into the code
4. View live graphs and trends on your ThingSpeak dashboard

---

## 🌍 Sustainable Development Goals (SDGs)

| SDG | Goal | How This Project Contributes |
|---|---|---|
| SDG 6 | Clean Water & Sanitation | Prevents contaminated water from being packaged |
| SDG 9 | Industry, Innovation & Infrastructure | Low-cost embedded system for industrial automation |
| SDG 12 | Responsible Consumption & Production | Reduces wastage through real-time fault detection |

---

## 🆚 Existing Solutions vs This Project

| Feature | PLC/SCADA (Large Industry) | Manual Testing (Small Industry) | This Project |
|---|---|---|---|
| Real-time monitoring | Yes | No | Yes |
| Cost | Very High | Low | Low |
| Continuous operation | Yes | No | Yes |
| Automatic alerts | Yes | No | Yes |
| Cloud visualization | Sometimes | No | Yes |
| Compact PCB design | No | No | Yes |

---

## 🚀 Future Scope

- **Mobile App Integration** — push notifications for alarm events
- **GPS Tagging** — log location of each monitoring node
- **Machine Learning** — predict water quality degradation trends
- **Solar Power** — enable off-grid remote water source monitoring
- **Multi-Node Network** — monitor multiple water sources simultaneously
- **Flow Sensor** — measure water flow rate alongside quality parameters

---

## 📄 License

This project is open source and free to use for educational and research purposes.

---

⭐ If you found this project helpful, please give it a star!
