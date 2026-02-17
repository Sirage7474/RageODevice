# RageODevice

A custom macro keyboard built around the Arduino Pro Micro (ATmega32U4) with an OLED display, rotary encoder, and 4 programmable buttons. Configure everything via a web-based configurator — no software installation required.

---

## Hardware

| Component | Details |
|-----------|---------|
| Microcontroller | Arduino Pro Micro (ATmega32U4) |
| Display | SSD1315 OLED 128x64 (I2C) |
| Encoder | EC11 Rotary Encoder |
| Buttons | 4x tactile switches (matrix) |

### Pinout

| Pin | Function |
|-----|----------|
| 2 | Button S1 |
| 3 | Button S2 |
| 4 | Button S3 |
| 5 | Button S4 |
| 6 | Button Common (GND) |
| 18 | Encoder Switch |
| 19 | Encoder B |
| 20 | Encoder A |
| 0 | OLED SDA (I2C) |
| 1 | OLED SCL (I2C) |

---

## Features

- 4 fully programmable buttons (80 keys and shortcuts available)
- Rotary encoder with 3 modes: **Volume**, **Zoom**, **Scroll**
- Encoder click: mute / reset zoom depending on mode
- Hold encoder 1.5s to enter settings menu
- OLED display showing current state and settings menu
- Click counter per button (viewable in settings)
- Settings saved to EEPROM (persist after power loss)
- 3 second menu timeout (auto-returns to idle)
- Web configurator for live configuration via USB

---

## Web Configurator

The web configurator runs in the browser and sends configuration to the device over USB Serial. No drivers or software needed.

**Requirements:**
- Chrome or Edge (Web Serial API required)
- Firefox and Safari are not supported

**How to use:**
1. Open `https://sirage7474.github.io/RageODevice` in Chrome or Edge
2. Connect your RageODevice via USB
3. Click **Connect Device** and select your device from the list
4. Configure your buttons and encoder mode
5. Click **Send to Device** — settings are saved to EEPROM instantly

### Preset System

The configurator supports saving and sharing presets as `.txt` files.

- **Save** — store a preset locally in the browser
- **Download .txt** — export your config as a text file to share
- **Import .txt** — load a preset file, settings apply instantly
- **Load / Delete** — manage your saved presets

Example preset file:
```
# RageODevice Preset
# NAME: Gaming Setup
# DATE: 1/1/2026

S1=0  # Space
S2=2  # ESC
S3=72  # Task Manager
S4=51  # Ctrl+C
ENC=0  # Volume
```

---

## Available Key Mappings

| Index | Key | Index | Key |
|-------|-----|-------|-----|
| 0 | Space | 42 | Up Arrow |
| 1 | Enter | 43 | Down Arrow |
| 2 | ESC | 44 | Left Arrow |
| 3 | Backspace | 45 | Right Arrow |
| 4 | Tab | 46 | Page Up |
| 5 | Delete | 47 | Page Down |
| 6-25 | W A S D Q E R F G H J K L Z X C V B N M | 48 | Home |
| 26 | Shift | 49 | End |
| 27 | Ctrl | 50 | Insert |
| 28 | Alt | 51 | Ctrl+C |
| 29 | Win | 52 | Ctrl+V |
| 30-41 | F1 - F12 | 53 | Ctrl+X |
| 54 | Ctrl+Z | 65 | Alt+Tab |
| 55 | Ctrl+Y | 66 | Alt+F4 |
| 56 | Ctrl+S | 67 | Alt+Enter |
| 57 | Ctrl+A | 68 | Win+D |
| 58 | Ctrl+F | 69 | Win+E |
| 59 | Ctrl+P | 70 | Win+L |
| 60 | Ctrl+N | 71 | Win+R |
| 61 | Ctrl+W | 72 | Task Manager |
| 62 | Ctrl+T | 73 | Print Screen |
| 63 | Ctrl+Tab | 74 | Mute |
| 64 | Ctrl+Shift+T | 75 | Volume Up |
| | | 76 | Volume Down |
| | | 77 | Play/Pause |
| | | 78 | Next Track |
| | | 79 | Prev Track |

---

## Flashing the Firmware

Flashing is done via the web configurator — no Arduino IDE required.

1. Open `RageODevice.html` in Chrome or Edge
2. Connect your RageODevice via USB
3. Click **Connect Device** and select your device
4. Configure your buttons and encoder mode
5. Click **Send to Device** — settings are saved to EEPROM instantly

> Note: The web configurator only sends configuration data (button mappings, encoder mode).
> For uploading new firmware you still need Arduino IDE.

---

## Flashing the Firmware

1. Open `RageODevice.ino` in Arduino IDE
2. Select **Tools → Board → Arduino AVR Boards → Arduino Micro**
3. Select the correct COM port
4. Click **Upload**

### Custom Device Name (Optional)

To make the device appear as **RageODevice** on every computer:

1. Find your `boards.txt` file:
   ```
   C:\Users\[name]\AppData\Local\Arduino15\packages\arduino\hardware\avr\[version]\boards.txt
   ```
2. Find and change these two lines:
   ```
   micro.name=RageODevice
   micro.build.usb_product="RageODevice"
   ```
3. Save the file, restart Arduino IDE and re-flash

---

## EEPROM Memory Map

| Address | Data |
|---------|------|
| 0 | Button S1 mapping |
| 1 | Button S2 mapping |
| 2 | Button S3 mapping |
| 3 | Button S4 mapping |
| 10 | Encoder mode (0=Volume, 1=Zoom, 2=Scroll) |
| 20-35 | Click counters (4x unsigned long) |

---

## Settings Menu

Hold the encoder button for **1.5 seconds** to enter the settings menu.

- Rotate encoder to navigate
- Click encoder to select
- Menu auto-closes after **3 seconds** of inactivity
- Settings are saved to EEPROM on exit

### Menu Options
- **S1 / S2 / S3 / S4** — change the key mapping for each button
- **Clicks** — view the click count for each button
- **Exit** — save and return to idle screen

---

---

## License

MIT License — free to use, modify and share.
