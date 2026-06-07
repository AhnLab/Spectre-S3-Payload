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
