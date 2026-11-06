# ESP32 Receiver Node & GPIO Diagnostic Firmware

[![Platform](https://img.shields.io/badge/Platform-PlatformIO-orange.svg)](https://platformio.org/)
[![Hardware](https://img.shields.io/badge/Hardware-ESP32--DevKit-blue.svg)](https://www.espressif.com/)
[![Category](https://img.shields.io/badge/Category-Diagnostics-blueviolet.svg)](https://github.com/)

A diagnostic and bring-up firmware for the ESP32 receiver node in the multi-sensor IR traffic detection and telemetry suite. It confirms board power regulation, system clock stability, bootloader health, and serial transmission over the USB UART interface at 115200 baud.

---

## Features

- **Heartbeat Signal**: Drives the on-board status LED on `GPIO 2` with 1-second pulse intervals.
- **Serial Diagnostics**: Transmits regular runtime status over the primary hardware UART port for cable and driver validation.
- **Scaffolding Framework**: Serves as a validated reference node for expanding multi-channel infrared sensor arrays and inter-board communications.

---

## Hardware Configuration

| Pin | Assignment | Description |
| :--- | :--- | :--- |
| `GPIO 2` | Status LED | Built-in LED on ESP32 DevKit modules |
| `UART0 TX/RX` | USB Serial | Serial diagnostics at 115200 baud |

---

## PlatformIO Configuration

From [`platformio.ini`](platformio.ini):

```ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = arduino
```

---

## Building and Flashing

```bash
# Compile firmware
pio run

# Upload to ESP32
pio run --target upload

# Monitor serial stream
pio device monitor -b 115200
```

---

## Project Structure

```
esp  reciever 6 ir/
├── src/
│   ├── main.cpp         # Core diagnostic blink and serial test loop
│   └── test.cpp         # Auxiliary testing scratchpad
└── platformio.ini       # PlatformIO environment specification
```

---

## License

MIT License.
