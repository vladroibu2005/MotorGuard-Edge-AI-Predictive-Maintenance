# MotorGuard — Edge AI Predictive Maintenance

> A low-power predictive maintenance system for small electric motors using the Nordic Semiconductor nRF54LM20 DK, Edge AI, sensors, and Bluetooth Low Energy.

![Project Status](https://img.shields.io/badge/status-planned-yellow)
![Platform](https://img.shields.io/badge/platform-nRF54LM20-blue)
![AI](https://img.shields.io/badge/AI-Edge%20AI-green)
![Connectivity](https://img.shields.io/badge/connectivity-Bluetooth%20LE-blue)

---

## Overview

MotorGuard is a planned Edge AI predictive maintenance system designed to detect early signs of degradation in small electric motors.

Instead of waiting for a motor to fail or relying only on fixed maintenance intervals, MotorGuard will continuously monitor the motor's physical behavior using sensors such as an accelerometer and temperature sensor.

The sensor data will be processed locally by the **Nordic Semiconductor nRF54LM20**, using an on-device machine learning model to identify abnormal operating patterns.

When an anomaly is detected, the system will communicate the motor's health status and a maintenance recommendation to a connected device using **Bluetooth Low Energy**.

The goal is to demonstrate how low-power Edge AI can help extend equipment lifetime, reduce unnecessary maintenance, minimize downtime, and reduce material waste.

---

## Problem

Small electric motors and other equipment are commonly maintained either according to fixed schedules or after a noticeable failure occurs.

Both approaches have limitations:

- Healthy components may be replaced unnecessarily.
- Developing mechanical problems may remain unnoticed.
- Unexpected failures can cause downtime.
- Maintenance and replacement can consume additional materials and energy.

MotorGuard aims to detect changes in motor behavior early, before they develop into a more serious failure.

---

## How It Works

The planned system follows this pipeline:

```text
      Small DC Motor
             │
             ▼
   ┌───────────────────┐
   │     Sensors       │
   │                   │
   │  • Vibration      │
   │  • Temperature    │
   └─────────┬─────────┘
             │
             ▼
   ┌───────────────────┐
   │   nRF54LM20 DK    │
   │                   │
   │ Sensor acquisition│
   │ Signal processing │
   │     Edge AI       │
   │   Health analysis │
   └─────────┬─────────┘
             │
        Bluetooth LE
             │
             ▼
   ┌───────────────────┐
   │   Phone / PC      │
   │                   │
   │ Health status     │
   │ Anomaly alerts    │
   │ Maintenance advice│
   └───────────────────┘
```
The system will first establish what normal motor operation looks like. It will then continuously compare new sensor data against this learned behavior.

The expected operating states are:

```text
NORMAL
   ↓
WARNING
   ↓
CRITICAL
```
Main Features:
Real-time motor vibration monitoring
Motor temperature monitoring
Edge AI anomaly detection
Local processing on the nRF54LM20
Motor health assessment
Early degradation detection
Bluetooth Low Energy communication
Maintenance alerts and recommendations
Low-power embedded operation
Controlled degradation testing
Edge AI

The machine learning component is intended to detect deviations from the motor's normal operating behavior.

The planned workflow is:
```text
Sensor Data
     │
     ▼
Data Collection
     │
     ▼
Signal Processing
     │
     ▼
Feature Extraction
     │
     ▼
ML Model Development
     │
     ▼
Model Deployment
     │
     ▼
nRF54LM20 Edge Inference
```
Possible vibration features include:

RMS
Mean
Variance
Standard deviation
Peak values
Peak-to-peak amplitude
Frequency-domain features

The exact model and feature set will be determined during development and testing.

The initial approach will focus on anomaly detection, allowing the system to learn the characteristics of healthy operation and identify significant deviations.

Bluetooth Low Energy

Bluetooth Low Energy will provide the wireless communication link between the MotorGuard device and a connected phone or computer.

Rather than continuously transmitting large amounts of raw sensor data, the system is planned to communicate relevant information such as:
```text
Motor Status: WARNING

Temperature: 47.2 °C
Vibration: 1.84 g
Anomaly Score: 0.73

Recommendation:
Inspect motor
```
This allows the embedded system to perform the analysis locally while using Bluetooth primarily for monitoring and user notification.

Hardware
Planned Hardware
Nordic Semiconductor nRF54LM20 DK
3-axis accelerometer
Temperature sensor
Small brushed DC motor
DC motor driver
External motor power supply
Breadboard and jumper wires
Basic electronic components
Possible Future Addition
Motor current sensor

Current sensing may be added later to provide an additional source of information for sensor fusion.

Why the nRF54LM20?

The nRF54LM20 is planned to serve as the central processing and communication platform of MotorGuard.

The project will use the development kit for:

Sensor data acquisition
Local signal processing
Edge AI inference
Motor health analysis
Bluetooth Low Energy communication

The nRF54LM20B's integrated NPU is particularly relevant to the project's Edge AI component, allowing the predictive maintenance workload to be explored directly on the embedded device rather than relying entirely on a remote computer or cloud service.

Predictive Maintenance Demonstration

The final prototype is planned to demonstrate progressive motor degradation.

Stage 1 — Healthy Operation

The motor operates normally and sensor data is collected to establish a baseline.

Stage 2 — Controlled Degradation

A controlled mechanical change will be introduced to alter the motor's behavior.

Examples may include:

Mechanical imbalance
Increased friction
Additional mechanical load
Other controlled vibration changes
Stage 3 — Anomaly Detection

The system should identify that the motor's behavior has changed compared with its healthy baseline.

Stage 4 — Maintenance Alert

The nRF54LM20 will classify the condition as a warning or critical state and communicate the result over Bluetooth.

The goal is to detect the developing problem before a simulated failure occurs.

Development Plan
Phase 1 — Hardware Setup
Set up the nRF54LM20 DK
Connect the accelerometer
Connect the temperature sensor
Set up the DC motor and motor driver
Phase 2 — Sensor Data Collection
Acquire vibration data
Acquire temperature data
Establish a healthy motor baseline
Store data for analysis
Phase 3 — Signal Processing
Filter sensor data where necessary
Create analysis windows
Extract relevant features
Visualize the collected data
Phase 4 — Machine Learning
Prepare the dataset
Train an anomaly detection model
Validate the model using controlled motor conditions
Select a model suitable for embedded inference
Phase 5 — Edge AI Deployment
Deploy the selected model to the nRF54LM20
Perform inference locally
Optimize memory, processing time, and power consumption
Phase 6 — Bluetooth Integration
Define the BLE data structure
Transmit motor health information
Implement anomaly notifications
Phase 7 — Final Demonstration
Demonstrate healthy operation
Introduce controlled degradation
Detect the resulting anomaly
Send a maintenance recommendation over BLE
