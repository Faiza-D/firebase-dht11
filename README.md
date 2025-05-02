Here's a concise and clear **README** you can include with your `Lab11: Firebase-1` folder:

---

# 💡 Lab 11: ESP32-S3 + DHT11 + Firebase Realtime Database

This lab demonstrates how to connect an ESP32-S3 board with a **DHT11 temperature/humidity sensor** and send the data to **Firebase Realtime Database** every 10 seconds using HTTP requests.

---

## 📂 Folder Contents

* `firebase_dht11.ino`: Arduino code for ESP32-S3 to read DHT11 sensor and upload data to Firebase.
* `README.md`: Instructions and explanation for setting up Firebase, modifying the code, and uploading the project.

---

## 🚀 Features

* Reads temperature and humidity using DHT11 sensor.
* Connects ESP32-S3 to Wi-Fi.
* Sends sensor data to Firebase Realtime Database as JSON.
* Includes automatic error handling and reconnection.
* Uses non-blocking `millis()`-based timing.
* Firebase HTTP POST integration (no third-party libraries).
* Bonus Task: Replace `millis()` timestamp with **real-time NTP-based timestamp (Pakistan Standard Time)**.

---

## 🔧 Firebase Setup (Summary)

1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com).
2. Enable **Realtime Database** → Start in test mode.
3. Copy your Firebase **Database URL** and **Secret Key**.
4. Set rules to:

   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
   ```
5. Replace placeholders in the Arduino code:

   * `const char* ssid = "YOUR_WIFI_SSID";`
   * `const char* password = "YOUR_WIFI_PASSWORD";`
   * `FIREBASE_HOST = "YOUR-PROJECT-ID.firebaseio.com";`
   * `FIREBASE_AUTH = "YOUR-DATABASE-SECRET";`

---

## 📦 Required Arduino Libraries

Install via **Library Manager**:

* `DHT sensor library by Adafruit`
* `WiFi` (comes with ESP32 board support)
* `HTTPClient` (comes with ESP32 board support)

---

## ⏱️ Bonus Task

Update the timestamp in the JSON payload to use **real-time** in **Pakistan Standard Time (UTC+5)** using an NTP library like:

```cpp
#include <NTPClient.h>
#include <WiFiUdp.h>
```

Replace `millis()/1000` with a formatted NTP timestamp in `sendToFirebase()`.

---

## 📡 Upload & Monitor

1. Select **Board**: `ESP32S3 Dev Module`
2. Connect ESP32-S3 via USB
3. Upload the sketch
4. Open **Serial Monitor** at `115200 baud`
5. Check Firebase Console → Realtime Database for incoming data

