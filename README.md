# 🚀 Fire and Gas Leak Monitoring System

This project is an intelligent safety monitoring system developed as an integrated hardware-software solution using **Arduino** and **Python**. The system provides multi-layered protection by combining real-time physical sensor data with computer vision-based fire and smoke detection.

---

## 🛠️ System Architecture

### 1. Hardware Layer (Arduino)
The Arduino Uno serves as the central controller for the physical environment.
* **Sensors:** Continuously reads data from the DHT22 (temperature and humidity) and a gas sensor (analog and digital).
* **Rapid Response:** Uses an interrupt-driven structure (`attachInterrupt`) to provide instant responses to button presses and gas sensor triggers.
* **Data Communication:** Transmits processed sensor data to the Python interface via serial communication (9600 baud).
* **Alarm Management:** Triggers a physical LED alarm when safety thresholds (e.g., 27°C, 400 gas units) are exceeded.

### 2. Software Layer (Python)
The Python script acts as the command center for monitoring and logging.
* **Tkinter GUI:** A graphical interface that displays real-time environmental metrics and system status.
* **Computer Vision (OpenCV):** Processes live camera feed in the HSV color space to perform real-time flame and smoke detection.
* **Alerts & Logging:** Uses `pygame` to play specific alarm sounds and logs all events with timestamps into a `uyarilar_log.txt` file for historical traceability.

---

## ⚠️ Prerequisites & Hardware Requirements

This is a **hardware-software integrated project**. It **cannot function as intended without the following components**:

* **Arduino Uno:** Required to run the sensor logic and handle the alarm system.
* **Sensors:** DHT22 (Temperature/Humidity) and MQ series Gas Sensor.
* **Communication:** The system must be connected to the computer via a USB serial port (configured as `COM3` in the code).
* **Peripheral Hardware:** A physical reset button connected to pin 2 and a status LED on pin 5.

**Important Note:** The **core safety monitoring (sensor readings, real-time safety status, and physical alarm reset) requires the Arduino to be connected and running the provided source code.**



---

## 📦 Getting Started

### 1. Hardware Setup
* Connect your sensors and components to the Arduino Uno.
* Upload the `sourceCode_arduino.txt` to your Arduino using the Arduino IDE.
* Identify the Serial Port your Arduino is connected to (e.g., `COM3`).

### 2. Software Environment
Ensure you have Python installed, then install the required dependencies:
```bash
pip install opencv-python pyserial pygame pillow numpy
```

### 3. Configuration
* Open the `sourceCode_python.txt` file.
* Locate the line `ser = serial.Serial('COM3', 9600)` and update `COM3` to match your actual Arduino port.
* Ensure you have the required audio files (`yangin.mp3`, `gaz.mp3`, `sicaklik.mp3`) in your directory.

### 4. Running the System
1. Connect your Arduino to the computer via USB.
2. Execute the Python script:
```bash
python sourceCode_python.py
```

---

## 🚀 Key Features

* **Hybrid Security:** Multi-layered detection using both physical sensors and computer vision.
* **Automatic Activation:** Automatically initiates the camera system when high-temperature scenarios are detected.
* **Manual Control:** A physical button allows the user to reset the alarm status.
* **Detailed Logging:** Automatically captures the start and end times of all hazard events for auditability.
