# Vital Sign Monitoring Smart Shirt (VSM-3)

This project presents a wearable smart shirt system for real-time monitoring of physiological signals, including ECG, SpO₂, temperature, and motion.

The system integrates embedded hardware, Arduino firmware, and a local web-based dashboard for real-time visualization and data logging.

## System Overview

The VSM-3 system consists of three main components:

- **Wearable hardware** with embedded sensors
- **Arduino-based firmware** for data acquisition
- **Web dashboard** for real-time visualization

## Features

- Real-time ECG waveform visualization
- Heart rate estimation
- SpO₂ monitoring
- Body temperature tracking
- Motion detection using IMU
- Fully local operation (no cloud required)

---

## Repository Structure

```bash
hardware/        → CAD files and enclosure design
firmware/        → Arduino code for sensors
dashboard/       → Web dashboard (local visualization)
docs/            → Project poster and documentation
