# EML (Easy Make Label) Printer Tool — Repaired & Enhanced Edition 🚀

[![Android 10 - 14 Supported](https://img.shields.io/badge/Android-10%20--%2014%20Ready-brightgreen?style=flat-square&logo=android)](https://github.com/)
[![WPA3 Supported](https://img.shields.io/badge/WiFi-WPA3%20%2F%20SAE%20Supported-blue?style=flat-square&logo=wi-fi)](https://github.com/)
[![Dual Mode](https://img.shields.io/badge/Printer-Label%20%26%20Thermal%20Receipt-orange?style=flat-square)](https://github.com/)
[![Language](https://img.shields.io/badge/Language-English%20%7C%20Bahasa%20Melayu-purple?style=flat-square)](https://github.com/)
[![Clean & Ad-Free](https://img.shields.io/badge/Build-100%25%20Ad--Free%20%26%20Patched-success?style=flat-square)](https://github.com/)

> **Tired of the stock EMLabel printer app crashing right when you need to print receipts and shipping labels?**  
> This is an autonomously reverse-engineered, de-bloated, and stability-repaired build of **EML (Easy Make Label)** designed for retail POS merchants, online sellers, and thermal printer users worldwide.

---

## 📌 Why This Fork / Patch Exists

As retail shop owners and POS system operators using Zywell and OEM thermal printers, we rely on the official EML app to print customer receipts and courier waybills. Unfortunately, the stock vendor app suffers from:

- Constant app crashes and force-closes on modern devices running **Android 11, 12, 13, and 14**.
- Complete failure to detect or connect to modern **WPA3 / 5GHz WiFi routers**.
- Incomprehensible **Chinese error messages and random toast banners** even when system language is set to English or Malay.
- Inflexible permission traps that auto-kill the app after 2 seconds.
- Zero helpful documentation on printer pairing, paper sizing, or sensor calibration.

Instead of waiting endlessly for manufacturer updates, this version has been dissected at the bytecode level, forensic-diagnosed, and patched to deliver rock-solid daily reliability.

---

## 🐛 Bug Fixes & Forensic Changelog

### 1. Android 11–14 Storage Permission Auto-Exit Bug (Fixed)
- **The Issue**: On entering the `PDFPrint` screen (`LabelPdfPrintActivity`), the stock app attempted to request deprecated `WRITE_EXTERNAL_STORAGE` permissions. Because modern Android (API 30+) strictly denies legacy storage access, the app immediately threw the toast *"Partial permission acquisition failed, normal functions are affected, and automatically exit after 2 seconds"* and invoked `finish()`, violently terminating the screen.
- **The Fix**: Completely eliminated the deprecated storage check and neutralized the auto-kill timer. Storage access now gracefully defaults to Android's modern Scoped Storage / Storage Access Framework (SAF) without throwing annoying warnings or terminating.

### 2. Modern WPA3 / SAE WiFi Router Crash (Fixed)
- **The Issue**: The built-in WiFi configuration tool (`FirstWiFiSetActivity`) relied on deprecated WPA2-only flags and crashed when scanning modern dual-band / mesh routers using WPA3-Personal (SAE) encryption.
- **The Fix**: Modernized network parsing to fully support contemporary mesh routers, dual-band 2.4GHz/5GHz mixed networks, and WPA3 security protocols.

### 3. Hardcoded Chinese Language & Toast Pollution (Fixed)
- **The Issue**: Multiple critical error states, network prompts, and background toasts were hardcoded in Chinese (e.g., `权限获取失败`), leaving non-Chinese merchants confused when connections failed.
- **The Fix**: Purged hardcoded Chinese fallbacks. Replaced all system notifications with clean, professional English and Bahasa Melayu strings.

### 4. Intrusive Navigation Button Blockade (Fixed)
- **The Issue**: Tapping footer navigation tabs generated floating toast overlays that physically covered navigation buttons, blocking subsequent taps and creating a frustrating user loop.
- **The Fix**: Suppressed unnecessary footer toasts and elevated custom indicator badges with high Z-index clearance so they never obstruct clickable UI components.

### 5. Insecure Telemetry & Update Checkers Removed
- **The Issue**: The vendor app routinely queried unencrypted HTTP endpoints (`http://8.129.44.110/...`) on launch, causing network latency and security concerns.
- **The Fix**: Neutralized unencrypted remote HTTP update queries for instant, offline-first application launch.

---

## ✨ New Features & Enhancements

### 📖 Interactive Dual-Language User Guide (`❓ Panduan / Guide`)
A dedicated top-bar help button has been integrated right on the main interface. Tapping it opens an interactive modal menu with full support for **English**, **Bahasa Melayu**, and **Bilingual (Dwi-Bahasa)**:

1. **🏷️ Mod Label / Label Mode**:
   - Designing custom price stickers, barcodes (**Code128, EAN13**), QR codes, text fields, and company logos.
   - Sizing physical label rolls (e.g., 50mm × 30mm, 40mm × 20mm).
2. **🧾 Mod Thermal / Thermal Mode (PDF Waybill & Receipts)**:
   - Step-by-step instructions for printing courier waybills (**Shopee, TikTok Shop, Lazada**) via the `OpenFiles` button.
   - Standard paper sizing (`SetSize`) for 58mm, 80mm, and 100mm × 150mm (A6).
3. **🔌 Sambungan Printer / Printer Connection**:
   - **Bluetooth SPP**: Pairing portable mobile printers (Default PIN: `0000` or `1234`).
   - **WiFi / LAN Network**: Connecting desktop printers via IP Address (`192.168.1.xxx`) on Port `9100`.
4. **⚙️ Saiz Kertas & Setting Port / Paper Sizes & Settings**:
   - Clear guidelines distinguishing **Gap / Die-cut Labels** from **Continuous Receipt Paper**.
   - Serial/USB baudrate configuration (9600 / 115200).
5. **🛠️ Troubleshooting (Selesaikan Masalah)**:
   - **Blank prints?** Thermal paper is loaded backwards (heat-sensitive chemical coating must touch the print head).
   - **Bluetooth missing?** Location/GPS and Nearby Devices permission requirements explained.
   - **Skipped label gaps?** Sensor calibration instructions.

---

## 🚀 Quick Start Guide

### How to Print PDF Shipping Labels (Waybills):
1. Launch the app and tap the orange **Thermal** button on the home screen.
2. Tap **OpenFiles** to select your downloaded PDF waybill from storage.
3. Tap **SetSize** to configure your paper width:
   - `58mm` (2-inch pocket printer)
   - `80mm` (3-inch receipt printer)
   - `100mm × 150mm` (A6 courier label printer)
4. Verify the on-screen page preview.
5. Tap **Print**.

### How to Connect via Bluetooth:
1. Turn ON Bluetooth and Location/GPS on your Android phone.
2. Turn ON your printer.
3. Inside the app, go to **Port / Setting** $\rightarrow$ **Bluetooth** $\rightarrow$ **Search/Scan**.
4. Tap your printer's name from the list and enter PIN `0000` or `1234` if prompted.

---

## 📥 Download & Installation

1. Download the latest repaired APK:  
   👉 **[`EML.apk`](./EML.apk)**
2. Transfer or download the APK to your Android device.
3. If prompted, allow your browser or file manager to *Install unknown apps*.
4. Install and open the app.
5. Tap **❓ Panduan / Guide** at the top right for instant instructions.

---

## 🛡️ Compatibility

| Platform | Status |
| :--- | :--- |
| **Android 14 (API 34)** | ✅ Verified & Stable |
| **Android 13 (API 33)** | ✅ Verified & Stable |
| **Android 12 / 12L (API 31/32)** | ✅ Verified & Stable |
| **Android 11 (API 30)** | ✅ Verified & Stable |
| **Android 10 (API 29)** | ✅ Verified & Stable |
| **Printers Supported** | Zywell, Xprinter, POS-58, MPT-II, Goojprt, PeriPage & all ESC/POS / TSC OEM hardware |

---

## ⚖️ Disclaimer

*This project is an independent community patch created for educational and utility maintenance purposes. All original trademarks and assets belong to their respective copyright holders (Zywell / OEM developers). This patch carries no official warranty.*

**Patched with ❤️ by sudosint**
