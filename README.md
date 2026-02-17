# RageODevice Configurator

Custom web configurator for the **RageODevice macro keyboard**.\
Configure buttons, rotary encoder, presets and send settings directly to
your device via USB.

Works fully in browser using **Web Serial API** --- no software install
needed.

------------------------------------------------------------------------

# ✨ Features

### 🎛 Device Config

-   Configure **4 macro buttons (S1--S4)**
-   Choose from **100+ keyboard shortcuts**
-   Rotary encoder modes:
    -   Volume
    -   Zoom
    -   Scroll
-   Send settings directly to device (EEPROM save)

### 💾 Preset System

-   Save presets locally in browser
-   Load presets instantly
-   Delete presets
-   Download preset as `.txt`
-   Import `.txt` preset files
-   Share presets with others

### 🔌 USB Connection

-   Connect directly via browser
-   Web Serial (115200 baud)
-   Animated connection UI
-   Flash progress bar when sending settings

### 🖥 Clean UI

-   OLED screen preview
-   Rotary visual indicator
-   Smooth animations
-   Dark futuristic design
-   Toast notifications

------------------------------------------------------------------------

# 🧰 Requirements

## Browser support

Works ONLY in browsers with Web Serial support: - Google Chrome -
Microsoft Edge

Not supported: - Firefox - Safari

## Hardware

-   RageODevice
-   USB cable
-   Arduino firmware installed

------------------------------------------------------------------------

# 🚀 How to use

## 1. Open configurator

Open the HTML file in Chrome: RageODevice.html

No server needed.

## 2. Connect device

1.  Plug RageODevice via USB\
2.  Click **Connect Device**\
3.  Select port named RageODevice\
4.  Connected

## 3. Configure

-   Select shortcut for each button
-   Choose encoder mode (Volume, Zoom, Scroll)

## 4. Send to device

Click **Send to Device**

Settings are saved to EEPROM.

------------------------------------------------------------------------

# 💾 Presets

## Save preset

Type name → press Save\
Stored in browser.

## Download preset

Downloads .txt file you can share.

## Import preset

Load .txt preset from someone else.

------------------------------------------------------------------------

# 🧑‍💻 Arduino communication format

Configurator sends JSON: { "b1":0, "b2":2, "b3":72, "b4":0, "enc":1 }

Baud rate: 115200

Arduino must read JSON line and apply.

------------------------------------------------------------------------

# 🛠 Development

Everything is inside one file: - HTML - CSS - JS

Edit RageODevice.html to customize.

------------------------------------------------------------------------

# ⚠ Notes

-   Use Chrome or Edge
-   USB permission required
-   Settings stored in browser

------------------------------------------------------------------------

# 👑 RageODevice

Custom macro keyboard + rotary controller\
Built for speed, gaming and productivity.

------------------------------------------------------------------------

# License

Free to use and modify.
