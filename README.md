# AirSense – Hacked IKEA VINDRIKTNING Smart Air Monitor

AirSense is a modified version of the **IKEA VINDRIKTNING Air Quality Sensor** where the original hardware was **reverse-engineered and upgraded** with a **ESP8266 D1 Mini** running **ESPHome** to integrate it with **Home Assistant**.

Instead of using the stock LED-only indication from IKEA, this project exposes detailed environmental data, diagnostics, and device controls through a smart home dashboard.

This is a **hardware hacking + IoT integration project** designed to transform a simple air quality monitor into a fully connected environmental sensor.

---

# Project Overview

The original IKEA device contains a **PM1006 particulate matter sensor** but only shows air quality using a colored LED.

This project taps into the sensor's **UART interface** and adds a WiFi-enabled microcontroller to expose the data digitally.

Additional monitoring and diagnostics features were also implemented.

---

# Features

### Air Quality Monitoring

* PM2.5 concentration data
* Air quality classification (Good / Moderate / Poor)

### Smart Home Integration

* Direct integration with **Home Assistant**
* Real-time sensor updates
* Dashboard visualization

### Environmental Awareness

* Ambient light sensing with brightness percentage
* Raw voltage monitoring for calibration

### Device Monitoring

* WiFi signal strength monitoring
* Device uptime tracking
* ESP8266 internal temperature
* Free heap memory monitoring

### Hardware Status

* Fan activity detection
* Device online status monitoring

### Remote Control

* Remote restart button
* OTA firmware updates

### Network Diagnostics

* IP address reporting
* WiFi SSID information
* MAC address display

---

# Hardware Used

| Component                            | Purpose                                      |
| ------------------------------------ | -------------------------------------------- |
| IKEA VINDRIKTNING Air Quality Sensor | Base air quality monitor                     |
| ESP8266 D1 Mini                      | WiFi IoT controller                          |
| PM1006                               | Particulate Matter sensor (inside IKEA unit) |
| LDR                                  | Ambient light sensing                        |
| Voltage divider                      | Light measurement interface                  |

---

# Hardware Hack

The IKEA VINDRIKTNING internally contains a **PM1006 particulate matter sensor** connected via UART.

By opening the device and tapping into the sensor's **TX line**, the data can be read directly by the ESP8266.

Connections used:

| PM1006 | ESP8266 |
| ------ | ------- |
| TX     | D2 (RX) |
| GND    | GND     |
| VCC    | 5V      |

An **LDR circuit** was also added to measure ambient light conditions.

---

# ESPHome Sensors Exposed

The device publishes the following sensors:

| Sensor               | Description                           |
| -------------------- | ------------------------------------- |
| PM2.5 Concentration  | Air pollution level                   |
| Air Quality Status   | Good / Moderate / Poor classification |
| Light Sensor Voltage | Raw LDR voltage                       |
| Light Brightness     | Ambient brightness percentage         |
| WiFi Signal          | Network signal strength               |
| ESP8266 Temperature  | Internal chip temperature             |
| Free Heap            | Available memory                      |
| Uptime               | Device runtime                        |

Binary sensors:

| Sensor        | Description                       |
| ------------- | --------------------------------- |
| Fan Running   | Detects air purifier fan activity |
| Device Status | Online/offline status             |

---

# OTA Firmware Updates

Firmware can be updated remotely using **ESPHome OTA**, eliminating the need to reopen the device.

---

# Example Dashboard

When connected to **Home Assistant**, the device provides:

* Real-time air quality graph
* Light level monitoring
* Device health diagnostics
* Smart home automation triggers

---

# Possible Automations

Example automations enabled by this project:

* Turn on ventilation when PM2.5 exceeds threshold
* Dim dashboard screens when room becomes dark
* Notify when air quality degrades
* Monitor device health remotely

---

# Motivation

The stock **IKEA VINDRIKTNING Air Quality Sensor** only provides a basic LED indicator.

This project unlocks the full potential of the internal sensor by exposing real sensor data and integrating it into a smart home ecosystem.

---

# Future Improvements

Possible upgrades:

* AQI calculation using EPA standards
* Local display dashboard
* MQTT support
* Multi-room air quality mapping

---

# License

Open-source project for experimentation and learning.

---

# Author

Vipul Raj

IoT Developer | Hardware Hacker | Smart Home Enthusiast

---

# Useful Resources

ESPHome Documentation
[https://esphome.io](https://esphome.io)

Home Assistant Documentation
[https://www.home-assistant.io](https://www.home-assistant.io)
