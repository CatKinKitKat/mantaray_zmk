# Mantaray ZMK – Wireless Ergonomic Keyboard (Work in Progress)

**Mantaray ZMK** is an experimental wireless fork of the original Mantaray2040 keyboard. Inspired by the ZSA Voyager, this variant keeps the ergonomic layout but brings it into the wireless world by replacing the microcontroller and display. If you're looking for a compact, low-profile, column-staggered board with Bluetooth support — this build might be what you're after.

Maintained by: **CatKinKitKat**

---

## Key Differences from Original

- **RP2040 swapped for SuperMini (nRF52840 Pro Micro clone)**  
  → Brings Bluetooth LE and onboard LiPo charging  
- **OLED replaced with 160 mAh LiPo battery**  
  → Same physical footprint; fits snugly in OLED slot  
- **JST-PH battery connector added**  
  → Connected to VBAT and GND pads on the SuperMini  
- **Firmware changed from QMK to ZMK**  
  → Optimized for wireless, power management, and multi-device support

> This is a work in progress and evolving with each test build.

---

## Hardware (Target Bill of Materials)

- 1 x Mantaray PCB  
- 1 x SuperMini nRF52840 (Pro Micro-compatible)  
- 1 x 160 mAh LiPo battery (3.7 V, JST-PH 2-pin)  
- 1 x JST-PH battery connector (soldered to PCB)  
- 52 x Kailh hotswap sockets  
- 52 x Kailh Choc V1 switches  
- 52 x Choc-compatible low-profile keycaps  
- 52 x 1N4148 diodes (through-hole or SMD)  
- 1 x 3D-printed case (modified for battery clearance)  
- 8 x M2x5mm tapered head machine screws
- Reset button
- Optional:
  - 8 x M2x3x3.2 mm heat set inserts

---

## Power and Charging

The **SuperMini** includes a built-in LiPo charger that activates when connected via USB-C. No external charging circuitry is needed.

- Connect LiPo battery via JST-PH connector (VBAT to VBAT, GND to GND)
- USB-C provides:
  - Power to the board
  - Charging current (default ~100 mA; jumper enables up to 300 mA)
- Charging indicator LED onboard (varies by revision)

---

## Firmware: ZMK

This build uses [ZMK Firmware](https://zmk.dev), which supports Bluetooth LE, layers, combos, and deep sleep.

### Build Instructions

You'll need to set up the [ZMK development environment](https://zmk.dev/docs/development/setup).

Example build command:

```bash
west build -b nice_nano_v2 -- -DSHIELD=mantaray_zmk
