
This project utilizes a 24GHz radar sensor connected to an ESP32-C3 Mini microcontroller to monitor and report on four key states:

- **Distance**: Measures the distance of objects in centimeters.
- **Stationary Target**: Detects if an object is stationary.
- **Moving Target**: Detects if an object is in motion.
- **Presence**: Indicates whether any target (stationary or moving) is present.

The data is transmitted to Adafruit IO using the MQTT protocol for real-time visualization and monitoring. A configuration portal is included to allow users to easily update WiFi credentials, Adafruit IO username, and API key.

---

## Hardware Setup

### Components:
1. **24GHz Radar Sensor**
2. **ESP32-C3 Mini Microcontroller**
3. **Power Source** (5V via USB or battery)

### Connections:
The radar sensor connects to the ESP32-C3 Mini as follows:

| Radar Sensor Pin | ESP32-C3 GPIO Pin |
|------------------|-------------------|
| VCC              | VBUS              |
| GND              | GND               |
| Tx               | GPIO 4            |
| Rx               | GPIO 5            |
|

---

### Code Overview:
The code is divided into key sections:
1. **Radar Data Processing**: Reads the radar sensor's output signal to determine distance, stationary or moving targets, and presence.
2. **MQTT Communication**: Publishes data to Adafruit IO using distinct feeds for distance, stationary target, moving target, and presence. On AdafruitIO, create an account and create 4 feeds namely: distance, presence, movingTarget, stationaryTarget.
3. **Configuration Portal**: Sets up a web interface to input WiFi credentials, Adafruit username, and API key.

---

## Configuration Portal
The configuration portal is activated when the ESP32 fails to connect to the WiFi network. Here is how it works:

1. **Triggering the Portal**:
   - If WiFi connection fails, the ESP32-C3 Mini sets up an access point (AP) named `RadarConfigPortal`.
   - Connect your phone or computer to this AP.

2. **Accessing the Portal**:
   - Open a web browser and navigate to `192.168.4.1`.
   - You will see a simple interface to configure your WiFi SSID, password, Adafruit username, and API key.

3. **Saving Configuration**:
   - Enter the required details and click **Save**.
   - The ESP32 restarts and attempts to connect to the specified WiFi with the provided credentials.

