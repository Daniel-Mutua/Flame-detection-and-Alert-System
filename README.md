[esp_12_e_flame_sensor_readme.md](https://github.com/user-attachments/files/24946040/esp_12_e_flame_sensor_readme.md)
# ESP-12E Flame Sensor Web Dashboard

## Project Overview
This project uses an **ESP-12E (ESP8266)** module to create a **flame detection system** with a **web-based dashboard**. It monitors a flame sensor and triggers an LED and buzzer whenever a flame is detected. The sensor readings and device statuses are displayed on a responsive web page, allowing real-time monitoring and control.

---

## Features
- **Flame detection** using an analog flame sensor (A0).  
- **Visual alert** using an LED (connected to D1).  
- **Audible alert** using a buzzer (connected to D5 for safe GPIO use).  
- **Web dashboard** displaying sensor readings and device statuses.  
- **Interactive controls** to manually turn LED and buzzer ON/OFF.  
- Responsive web interface accessible via the ESP's IP on any browser.  

---

## Hardware Required
- ESP-12E (ESP8266) module  
- Flame sensor (analog output)  
- LED  
- Buzzer  
- Resistors (as needed for LED/buzzer)  
- Breadboard and jumper wires  
- USB cable for programming the ESP-12E  

**Pin Connections:**
| Component       | ESP Pin  |
|-----------------|----------|
| Flame Sensor    | A0       |
| LED             | D1 (GPIO5) |
| Buzzer          | D5 (GPIO14) |

---

## Software Required
- Arduino IDE (with **ESP8266 board package** installed)  
- ESP8266WiFi library  
- ESP8266WebServer library  

---

## Code Overview
- `setup()`  
  - Initializes serial communication for debugging.  
  - Connects to the Wi-Fi network.  
  - Sets up GPIO pins for LED and buzzer.  
  - Starts the web server and configures routes.  

- `loop()`  
  - Reads the flame sensor analog value.  
  - Compares it with a predefined threshold (`flameThreshold`).  
  - Turns LED and buzzer ON/OFF automatically based on flame detection.  
  - Handles incoming web client requests (`server.handleClient()`).  

- **Web Dashboard**  
  - Displays flame sensor value and flame status (Detected / No Flame).  
  - Shows current state of LED and buzzer.  
  - Provides interactive buttons to manually control LED and buzzer.

---

## How to Use
1. Connect the ESP-12E and peripherals as shown above.  
2. Open the Arduino IDE and select the correct **board** (NodeMCU 1.0 / ESP-12E) and **port**.  
3. Upload the code to the ESP-12E.  
4. Open the Serial Monitor at **115200 baud** to see Wi-Fi connection status and IP address.  
5. In a browser connected to the same network, go to:  
   ```
   http://<ESP_IP_ADDRESS>
   ```  
   Example: `http://192.168.1.10`  
6. Monitor flame sensor readings and control LED/Buzzer from the web page.

---

## Notes
- Ensure the ESP-12E and your PC or phone are on the **same Wi-Fi network** (2.4 GHz recommended).  
- Avoid using D8 (GPIO15) for outputs — it can interfere with boot. Use D5, D6, or D7 instead.  
- The flame detection threshold (`flameThreshold`) may need calibration depending on your sensor and environment.  

---

## Troubleshooting
- **Cannot connect to ESP IP?**  
  - Check router settings for AP/client isolation.  
  - Try using a mobile hotspot for testing.  
  - Ensure ESP is on 2.4 GHz Wi-Fi.  

- **ESP not booting properly?**  
  - Verify GPIO pins for LED and buzzer are safe (avoid D8/D0/D2 for outputs at boot).  
  - Check power supply; ESP8266 is sensitive to weak USB power.  

---

## License
This project is **open-source** and free to use under the MIT License.

