# Educational Framework: ESP32-S3 Wireless Security Analysis & Captive Portal Mechanics

This repository contains the firmware configurations, memory optimization profiles, and structural documentation for deploying a wireless security research lab on the ESP32-S3 architecture. Developed for academic demonstrations, this framework provides computer science students and security researchers with a hands-on environment to study 802.11 beacon management, localized DNS redirection, and modern operating system captive portal detection mechanisms.

**Author:** Usman Liaqat  
**Target Architecture:** ESP32 / ESP32-S3 (N16R8 Hardware Profile)  
**Academic Focus:** Embedded Systems Architecture, Wireless Network Security, Localized Network Routing  
**License:** MIT License  

---

## ⚠️ ACADEMIC & EDUCATIONAL USE ONLY
This project is designed strictly for authorized educational research, university laboratory exercises, and defensive wireless auditing. Operating captive networks or simulating alternative network profiles without explicit, written authorization from the infrastructure owner is illegal and violates wireless communications regulations. The author assumes no liability for external misuse or real-world operational disruption.

---

## ⚡ Core Functional Features
* **Multi-Architecture Compilation:** Fully compatible with standard ESP32 baseline models and highly optimized for dual-core ESP32-S3 systems.
* **Dual-Radio Emulation:** Supports simultaneous Access Point (AP) and Station (STA) environments to demonstrate network discovery and channel assessment mechanics.
* **DNS Redirection Engine:** Features a lightweight, localized DNS server configured to intercept external address resolutions and handle captive portal assistant queries.
* **High-Capacity Persistent Storage:** Utilizes internal Flash filesystems (SPIFFS/FATFS) to maintain offline configuration parameters, static styling assets, and structural transaction logs.
* **Asynchronous Web Interface:** Uses a responsive, mobile-optimized administration dashboard for real-time interaction, scanning operations, and data management.

---

## 🛠 Hardware Mapping Matrix

| Architectural Component | Baseline Minimum Specification | Advanced Lab Specification (Recommended) |
| :--- | :--- | :--- |
| **Microcontroller** | ESP32 (Xtensa Dual-Core LX6) | ESP32-S3 (Xtensa Dual-Core LX7 @ 240MHz) |
| **Wireless Interface** | 2.4GHz 802.11 b/g/n | 2.4GHz 802.11 b/g/n with Extended Channel Selection |
| **Physical Flash Storage**| 4MB (32Mb) | 16MB (128Mb) High-Speed Quad/Octal SPI |
| **External Volatile RAM**| None (Uses internal SRAM) | 8MB Octal SPI (OPI) PSRAM |
| **Data Interface** | Standard Micro-USB | Dual Type-C (Native Hardware USB CDC/JTAG) |

---

## ⚙️ Arduino IDE Tools Menu Configuration

| Tool Selection Option | Parameter Setting | Operational Purpose & Notes |
| :--- | :--- | :--- |
| **Board** | "ESP32S3 Dev Module" | Targets correct architecture and compilation compiler flags |
| **USB CDC On Boot** | "Disabled" | Maintains standard hardware serial initialization routines |
| **CPU Frequency** | "240MHz (WiFi)" | Provides optimal processing overhead for web serving |
| **Core Debug Level** | "None" | Minimizes serial terminal lag during multi-client parsing |
| **Erase All Flash Before Sketch Upload** | "Enabled" | Mandatory on first run to build filesystem |
| **Flash Mode** | "DIO 80MHz" | Resolves high-density 16MB memory stability anomalies |
| **Flash Size** | "16MB (128Mb)" | Registers full physical memory address boundaries |
| **Partition Scheme** | "16M Flash (3MB APP/9.9MB FATFS)" | Allocates generous space for assets and localized logging |
| **PSRAM** | "OPI PSRAM" | Maps the 8MB external volatile buffer for connection handling |
| **Upload Speed** | "115200" | Standard, noise-resilient firmware transfer rate |

---

## 🚀 Installation & Lab Deployment

### 1. IDE Environmental Setup
1. Download and open the Arduino IDE (Version 2.3.9 or higher recommended).
2. Navigate to **File > Preferences** and add the official Espressif board manager URL into the "Additional boards manager URLs" field:
   `https://dl.espressif.com/dl/package_esp32_index.json`
3. Open **Tools > Board > Boards Manager**, search for `esp32` by Espressif, and click **Install**.

### 2. Firmware Compilation & Flashing
1. Open the primary project file `Wireless_Security_Suite.ino` within the IDE environment.
2. Interface your ESP32-S3 module to your workstation using the dedicated UART/USB port.
3. Choose the appropriate active device port under **Tools > Port**.
4. Cross-reference your IDE parameter settings with the Tools Menu Configuration Matrix above. Ensure **Erase All Flash Before Sketch Upload** is **Enabled** for the baseline flash.
5. Click the **Upload** button to initiate compilation and map the partition tables.

---

## 📋 Standard Auditing Evaluation Procedure

### Step 1: Administrative Control Authentication
* Connect your evaluation workstation or mobile client to the management infrastructure network:
  * **Management SSID:** `WiFi_Pentest`
  * **Default Password:** `password123`
* Open an active web browser window and route traffic to the dedicated administrative dashboard endpoint: `http://192.168.4.1/admin`

### Step 2: Environmental Network Assessment
* Navigate to the **Scan** sub-panel interface to initiate an asynchronous environment pass.
* Analyze surrounding wireless infrastructure, noting active operating channels (Channels 1–13 supported), operational modes, and Received Signal Strength Indicators (RSSI).

### Step 3: Verifying Captive Portal Isolation
* Initialize the test routine via the control interface. The device will generate an unencrypted, open network matching the designated target parameters.
* Connect a test client device to assess how successfully the client's built-in operating system isolates traffic, handles the DNS redirection loop, and warns the user about insecure or untrusted captive portal endpoints.
* Review structural transactional access summaries within the **Captured Data** tab. Utilize the built-in purge commands to safely clear internal flash logs once the assessment criteria are satisfied.

* 
ESP32-S3 Evil Twin Captive Portal - Setup Guide

This repository contains the firmware and configuration settings for deploying an Evil Twin Captive Portal on an ESP32-S3 Development Board.

## 🛠 Hardware Specifications
* **Chip:** ESP32-S3 (Dual Core, 240MHz WiFi)
* **Flash Size:** 16MB (128Mb)
* **PSRAM:** 8MB (OPI PSRAM Configuration)

---

## ⚙️ Arduino IDE Tools Menu Configuration

To ensure the firmware compiles successfully and runs stably without cyclic reboots or crashes, you **must** configure your Arduino IDE `Tools` menu exactly as shown below. 

# Critical Settings Changed from Default:
1. **Flash Mode:** Changed from `QIO` to **`DIO 80MHz`** (Ensures correct timing and stability for the N16R8 flash interface).
2. **Flash Size:** Changed from `4MB` to **`16MB (128Mb)`** (Matches the physical capacity of the N16R8 module).
3. **Partition Scheme:** Changed from `Default 4MB` to **`16M Flash (3MB APP / 9.9MB FATFS)`** (Allocates 3MB for large application code and ~10MB for Captive Portal web assets/logs).
4. **PSRAM:** Changed from `Disabled` to **`OPI PSRAM`** (Enables the high-speed 8MB external RAM required for heavy buffer tasks).
5. **Erase All Flash Before Sketch Upload:** Changed from `Disabled` to **`Enabled`** (Mandatory for the first flash to clear any legacy partition tables and structure the FATFS filesystem).

### Full Configuration Reference Table:

| Tool Option | Selected Setting | Notes |
| :--- | :--- | :--- |
| **Board** | `"ESP32S3 Dev Module"` | Target Board |
| **USB CDC On Boot** | `"Disabled"` | Default |
| **CPU Frequency** | `"240MHz (WiFi)"` | Maximum Performance |
| **Core Debug Level** | `"None"` | Default |
| **USB DFU On Boot** | `"Disabled"` | Default |
| **Erase All Flash Before Sketch Upload** | **`"Enabled"`** | **[CHANGED]** Clears corrupt partition data |
| **Events Run On** | `"Core 1"` | Default |
| **Flash Mode** | **`"DIO 80MHz"`** | **[CHANGED]** Fixed stability/boot-loop issues |
| **Flash Size** | **`"16MB (128Mb)"`** | **[CHANGED]** Maps full 16MB capacity |
| **JTAG Adapter** | `"Disabled"` | Default |
| **Arduino Runs On** | `"Core 1"` | Default |
| **USB Firmware MSC On Boot** | `"Disabled"` | Default |
| **Partition Scheme** | **`"16M Flash (3MB APP/9.9MB FATFS)"`** | **[CHANGED]** Expanded app memory + file storage |
| **PSRAM** | **`"OPI PSRAM"`** | **[CHANGED]** Enables 8MB octal SPI RAM |
| **Upload Mode** | `"UART0 / Hardware CDC"` | Default |
| **Upload Speed** | `"115200"` | Stable Baud Rate |
| **USB Mode** | `"Hardware CDC and JTAG"` | Default |
| **Zigbee Mode** | `"Disabled"` | Default |

---

## 🚀 Flashing Instructions
1. Open the sketch `ESP32-Evil-Twin-Captive-Portal.ino` in Arduino IDE (v2.3.9 or higher recommended).
2. Connect your ESP32-S3 to your PC using the **UART/USB port**.
3. Select the correct COM port under `Tools -> Port`.
4. Double-check that **Erase All Flash Before Sketch Upload** is set to **Enabled**.
5. Click **Upload**.

*Note: After the first successful flash, you may change "Erase All Flash Before Sketch Upload" back to "Disabled" to prevent losing captured data logs on subsequent minor updates.*
