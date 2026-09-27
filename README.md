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
