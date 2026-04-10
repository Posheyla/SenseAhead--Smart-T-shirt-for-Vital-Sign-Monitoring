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
```

---
## 🚀 How to Run the VSM-3 System (USER GUIDE)

This guide explains how any user can run the system locally on their laptop and collect vital-sign data from the wearable shirt.

---
### 1️⃣ Hardware Setup (Wearable Shirt)

🔹 Required Components:

- Arduino UNO R4 WiFi

- MAX30101 (SpO₂ + HR)

- AD8232 (ECG)

- TMP117 (Temperature)

- ICM-20948 (9-axis IMU)

- Jumper wires

- Enclosure 3D printed parts (from CAD folder)

- Shirt with embedded sensors (as designed by team)


🔹 Assembly Overview:

- Attach all sensors to the Arduino using Qwiic/I2C and analog ECG connection

- Mount sensors inside the enclosure parts (CAD folder)

- Position electrodes on the chest and tighten straps

- Power the system via USB cable to the laptop

---

### 2️⃣ Upload Arduino Code

2.1. Open Arduino IDE

2.2. Open: firmware/web_arduino_2/web_arduino_2.ino

2.3. Scroll to the section:

```bash
//=======Wi fi config========
const char* STA_SSID = "YOUR_WIFI";
const char* STA_PASS = "YOUR_PASSWORD";
```
2.4. Change these values to match your hotspot name + password.

2.5. Connect Arduino UNO R4 WiFi with USB

Click:

✔ Verify
✔ Upload

2.6. Open Serial Monitor @ 115200 baud and confirm you see lines like:

```bash
ECG=700   Thr=400   motionScore=0.02   motionQuality=GOOD
```
This confirms the shirt is sending sensor data.

---

### 3️⃣ Launch the Web Dashboard (Local Mode)

3.1. The dashboard is located at: dashboard/webpage/public/index.html

3.2. To open the dashboard:

Open VS Code

Install the extension Live Server

Right-click: webpage/public/index.html

Select "Open With Live Server"

3.3. Your browser will open: http://127.0.0.1:5500/webpage/public/index.html

---

### 4️⃣ Create User Account (Local Authentication)

4.1. On the dashboard login page, select “Create account”

Enter:
```bash
Name
Email
Password
Log in
```

4.2. This works fully offline (local Firestore emulator).

---

### 5️⃣ Start Collecting Data

5.1. With Arduino running AND dashboard open:

✔ ECG plots appear

✔ Temperature updates

✔ SpO₂ shows when finger sensor works

✔ HR from ECG is averaged

✔ Motion score reflects IMU activity

---

### 6️⃣ Where Is Data Stored?

Even without Firebase, the dashboard stores data in: dashboard/webpage/export/

If Firebase is connected later, the same data is pushed to Firestore.

---

### 🛠 Developer Notes (for the team)

If deploying Firebase Functions again: 

Only the project owner can run: firebase deploy --only functions

Other teammates need IAM permission:

Service Account User in Google Cloud.

Normal users running data collection do NOT need Firebase.

---

### 🛠 Technologies Used

Arduino UNO R4 WiFi

Embedded systems

I2C sensors

JavaScript dashboard

Firebase (optional)

3D CAD design

---

### 👥 Authors

Artemis Badger

Luisa Chavez

Marc Dobos

Sultanus Salehin

Irem Yunculer

---

### 📄 License

This project is for educational use under ECE-522 (NC State University).
