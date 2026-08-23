# SamotPi2040 DevBoard

[![Hack Club Forge](https://img.shields.io/badge/Hack%20Club-Forge%20Project-ec3750?style=flat&logo=hackclub)](https://forge.hackclub.com/projects/1745)
[![KiCad](https://img.shields.io/badge/KiCad-v7%2B-blue?style=flat&logo=kicad)](https://www.kicad.org)
[![RP2040](https://img.shields.io/badge/MCU-RP2040-red?style=flat&logo=raspberrypi)](https://www.raspberrypi.com/products/rp2040/)

**SamotPi2040** is a custom, open-source Raspberry Pi RP2040 development board designed in KiCad. It breaks out the dual-core RP2040 microcontroller into a compact, breadboard-friendly form factor equipped with a modern USB-C interface, 8MB SPI flash memory, low-dropout voltage regulation, and onboard tactile buttons for instant firmware flashing and reset control.

---

## 📌 Project Overview & Purpose

- **What is it?** A standalone development board based on the Raspberry Pi RP2040 dual-core ARM Cortex-M0+ processor.
- **What does it do?** It provides all essential supporting circuitry (power regulation, high-speed crystal oscillator, SPI flash, USB termination, and ESD/pull-down configuration) to run MicroPython, CircuitPython, Arduino, or bare-metal C/C++ Pico SDK code.
- **Why does it exist?** It was created to explore custom PCB design from scratch, master multi-layer routing with fine-pitch QFN and 0402 components, and build a reliable, inexpensive, and customizable devboard for prototyping robotics and embedded electronics.

---

## 💡 Why I Made This Project

Most off-the-shelf development boards either use outdated Micro-USB connectors, lack dedicated hardware reset buttons, or come with fixed pin assignments that aren't ideal for every project. I wanted to design my own RP2040 board from the ground up to:
1. Deepen my understanding of high-speed differential USB routing, crystal load capacitance tuning, and power-distribution decoupling.
2. Add a modern **USB-C** connector with proper 5.1kΩ CC pull-down resistors for universal cable compatibility.
3. Integrate both **BOOTSEL** and **RESET** tactile switches directly on board to make rapid prototyping and flashing seamless without disconnecting cables.
4. Provide a full 8MB (64Mbit) high-speed SPI Flash storage for large CircuitPython scripts, assets, and datalogging.

---

## 🖼️ Project Gallery

### 3D Render
![Rendered PCB](images/rendered_PCB.png)

### 3D Board View
![3D PCB](images/3d_pcb.png)

### PCB Layout & Routing
![PCB Layout](images/pcb.png)

### Schematic
![Schematic Diagram](images/schematic.png)

---

## ⚙️ Hardware Features & Specifications

| Feature | Specification |
| --- | --- |
| **Microcontroller** | Raspberry Pi RP2040 (Dual-core ARM Cortex-M0+ up to 133 MHz, 264 KB on-chip SRAM) |
| **Flash Memory** | 8 MB (64 Mbit) SPI Flash (Macronix MX25L6433FM2I-08G, SOIC-8) |
| **Power Input** | USB-C 5V VBUS input |
| **Voltage Regulation** | Microchip MCP1700T-3302E/TT (3.3V Low-Dropout Regulator, 250mA output) |
| **Clock Source** | Abracon 12.000 MHz Crystal (ABM8G, SMD 3.2x2.5mm) with 27 pF load capacitors |
| **USB Interface** | GCT USB4085-GF-A 16-pin USB-C receptacle (USB 2.0 Full Speed with 27Ω series termination) |
| **Buttons** | SMD Tactile Switches (Omron B3U-1000P-B) for `BOOTSEL` (SW1) and `RESET` (SW2) |
| **Expansion / I/O** | 2x 1x20-pin 2.54mm pitch headers (breadboard compatible) + 1x 1x3-pin SWD debug header |

---

## 🛠️ Step-by-Step Assembly Guide

> [!IMPORTANT]
> This board uses fine-pitch surface-mount components (QFN-56 and 0402 passives). Using a **hot-air rework station** or a **mini reflow hot plate**, along with quality flux and solder paste, is strongly recommended.

### Required Tools
- Hot air rework station / Reflow hot plate & temperature-controlled soldering iron
- No-clean solder flux paste / pen and solder wick
- Precision fine-tip curved tweezers
- Isopropyl Alcohol (IPA >99%) and ESD brush for cleaning
- Digital Multimeter (for short-circuit and continuity checks)
- USB-C data cable

### Assembly Steps

1. **Solder the RP2040 MCU (U1 - QFN-56):**
   - Apply a thin layer of solder paste or flux to the center thermal ground pad and perimeter pads.
   - Carefully align pin 1 of the RP2040 chip using the silkscreen dot marker.
   - Reflow using hot air (~320°C–350°C) or hot plate. Ensure surface tension pulls the chip into alignment without bridges.
2. **Solder the SPI Flash (U3) and LDO Regulator (U2):**
   - Place and solder the MX25L6433 flash chip (SOIC-8) and the MCP1700 (SOT-23).
3. **Solder Passives (Resistors & Capacitors) and Crystal:**
   - Solder the 0402 decoupling capacitors (C1–C12, C17, C18) close to the RP2040 power pins.
   - Solder the 0603 bulk capacitors (C13, C14), crystal load capacitors (C15, C16), and resistors (R1–R7, R9).
   - Place and solder the 12 MHz crystal (Y1).
4. **Solder USB-C Receptacle (J1):**
   - Align the 16-pin USB-C receptacle (GCT USB4085). Solder the through-hole shielding legs for mechanical strength, then use a fine iron tip with plenty of flux to solder the SMD pins.
5. **Solder Pushbuttons (SW1, SW2):**
   - Solder the ultra-compact Omron B3U tactile switches for BOOTSEL and RESET.
6. **Pre-Power Inspection & Continuity Check:**
   - Inspect all solder joints under magnification for solder bridges or cold joints (especially on the RP2040 and USB-C).
   - Using a multimeter in continuity/resistance mode, verify that `VBUS` (5V), `3V3`, and `GND` are **not shorted**.
7. **Solder Pin Headers (J2, J3, J4):**
   - Insert the 1x20 2.54mm male headers into a solderless breadboard to keep them perpendicular, place the PCB on top, and solder each pin.
   - Solder the 1x3 SWD header (J4) if hardware debugging is required.

---

## ⚡ How to Flash Firmware

The RP2040 features a built-in ROM bootloader that makes flashing firmware simple without requiring external programmers:

```mermaid
flowchart LR
    A["Hold BOOTSEL"] --> B["Plug in USB-C"]
    B --> C["'RPI-RP2' Drive Appears"]
    C --> D["Drag & Drop .UF2 File"]
    D --> E["Auto Reboot & Run!"]
```

1. **Enter Bootloader Mode:**
   - Hold down the **`BOOTSEL`** button (SW1).
   - Connect the board to your computer using a USB-C data cable (or press and release **`RESET`** while holding `BOOTSEL`).
   - Release the `BOOTSEL` button.
2. **Mounting Drive:**
   - A removable USB storage volume named **`RPI-RP2`** will automatically appear on your operating system.
3. **Flashing Firmware:**
   - Drag and drop your compiled **`.uf2`** firmware file onto the `RPI-RP2` drive:
     - **MicroPython:** Download the [Official RP2040 MicroPython UF2](https://micropython.org/download/rp2-pico/).
     - **CircuitPython:** Download the [Adafruit CircuitPython RP2040 UF2](https://circuitpython.org/board/raspberry_pi_pico/).
     - **C/C++ SDK / Arduino:** Build your project using Arduino IDE (with Earle Philhower RP2040 core) or Pico SDK and drag the resulting `.uf2` file.
4. **Execution:**
   - Once the `.uf2` file finishes copying, the board will automatically dismount and execute the program immediately.

---

## 📋 Bill of Materials (BOM)

> Import [`quickOrder_TME.csv`](quickOrder_TME.csv) directly to [TME.eu](https://tme.eu) for rapid checkout.

| Qty | Value | Reference | Footprint | Part Number / Supplier | Approx. Cost (USD) |
|:---:|:---|:---|:---|:---|:---:|
| 1 | **RP2040** | U1 | QFN-56-1EP (7x7mm, 0.4mm pitch) | [Raspberry Pi SC0914-7 (TME)](https://www.tme.eu/cz/details/sc0914-7/raspberry-pi-vestavene-systemy/raspberry-pi/ic-rp2040-rp2b2-t-r-500-7-reel/) | $1.02 |
| 1 | **MX25L6433FM2I-08G** (8MB Flash) | U3 | SOIC-8 (5.3x5.3mm, 1.27mm pitch) | [Macronix (TME)](https://www.tme.eu/cz/details/mx25l6433fm2i-08g/pameti-flash-seriove/macronix-international/mx25l6433fm2i-08g-tube/) | $2.40 |
| 1 | **MCP1700T-3302E/TT** (3.3V LDO) | U2 | SOT-23 | [Microchip (TME)](https://www.tme.eu/cz/details/mcp1700t-3302e_tt/stabilizatory-napeti-neregulovane-ldo/microchip-technology/) | $0.65 |
| 1 | **12 MHz Crystal** | Y1 | SMD 3225-4Pin (3.2x2.5mm) | [Abracon ABM8G-12.000MHZ-18 (TME)](https://www.tme.eu/cz/details/abm8g-12.000mhz-18/resonators-and-generators/abracon/abm8g-12-000mhz-18-d2y-t/) | $0.39 |
| 1 | **USB-C Receptacle 16P** | J1 | GCT USB4085 | [GCT USB4085-GF-A (TME)](https://www.tme.eu/cz/details/usb4085-gf-a/konektory-usb-a-ieee1394/gct/) | $1.05 |
| 2 | **Tactile Switch SPST** | SW1, SW2 | SMD (Omron B3U-1000P-B) | [Omron B3U-1000PB (TME)](https://www.tme.eu/cz/details/b3u-1000pb/mikrospinace-tact/omron-electronic-components/b3u-1000p-b/) | $1.95 |
| 12 | **0.1 µF (100nF) 16V** | C2, C3, C4, C5, C6, C7, C8, C9, C11, C12, C17, C18 | C_0402 (1005 Metric) | [Murata GRM155R71C104KA88D (TME)](https://www.tme.eu/cz/details/grm155r71c104ka88d/kondenzatory-mlcc-smd/murata/) | $0.17 |
| 2 | **1 µF 25V** | C1, C10 | C_0402 (1005 Metric) | [Murata GRM155R61E105MA12D (TME)](https://www.tme.eu/cz/details/grm155r61e105ma12d/kondenzatory-mlcc-smd/murata/) | $0.095 |
| 2 | **10 µF 10V** | C13, C14 | C_0603 (1608 Metric) | [Taiyo Yuden LMK107BJ106MALTD (TME)](https://www.tme.eu/cz/details/lmk107bj106maltd/kondenzatory-mlcc-smd/taiyo-yuden/lmk107-bj106maltd/) | $0.30 |
| 2 | **27 pF 50V** | C15, C16 | C_0603 (1608 Metric) | [Yageo CC0603JRNPO9270 (TME)](https://www.tme.eu/cz/details/cc0603jrnpo9270/kondenzatory-mlcc-smd/yageo/cc0603jrnpo9bn270/) | $0.043 |
| 2 | **27 Ω 1%** | R3, R4 | R_0402 (1005 Metric) | [Panasonic ERJ2RKF27R0X (TME)](https://www.tme.eu/cz/details/erj2rkf27r0x/rezistory-smd/panasonic/) | $0.25 |
| 2 | **5.1 kΩ 1%** | R1, R2 | R_0603 (1608 Metric) | [Walsin WR06X5101FTL (TME)](https://www.tme.eu/cz/details/wr06x5101ftl/rezistory-smd/walsin/) | $0.18 |
| 2 | **1 kΩ 1%** | R5, R6 | R_0603 (1608 Metric) | [Vishay CRCW06031K00FKEA (TME)](https://www.tme.eu/cz/details/crcw06031k00fkea/rezistory-smd/vishay/) | $0.015 |
| 2 | **10 kΩ 1%** | R7, R9 | R_0603 (1608 Metric) | [Yageo RC0603JR-0710K (TME)](https://www.tme.eu/cz/details/rc0603jr-0710k/rezistory-smd/yageo/rc0603jr-0710kl/) | $0.085 |
| 2 | **Pin Header 1x20 (2.54mm)** | J2, J3 | PinHeader_1x20_P2.54mm_Vertical | Standard 2.54mm Pin Header | On hand |
| 1 | **Pin Header 1x3 (2.54mm)** | J4 | PinHeader_1x03_P2.54mm_Vertical | Standard 2.54mm Pin Header (SWD) | On hand |
| 5 | **Custom PCB (JLCPCB)** | PCB | 2-layer FR-4 (1.6mm, ENIG/HASL) | [JLCPCB](https://jlcpcb.com) | ~$13.45 |
| - | **Estimated Shipping** | - | - | - | ~$8.21 |
| **Total** | | | | | **~$30.76** |

### Fabrication Orders

<p align="center">
  <img src="images/jlcPcbcart.png" alt="JLCPCB Cart 1" width="48%">
  <img src="images/jlcPcbcart2.png" alt="JLCPCB Cart 2" width="48%">
</p>

---

## 🔍 Known Issues & Design Notes

1. **0402 Component Sizing:** The board uses 0402 passives for decoupling caps and USB series resistors to maintain a compact layout. Hand-soldering requires a fine tip (or hot air reflow) and high-magnification tweezers.
2. **Thermal Pad Reflow:** The central exposed ground pad (EP) under the RP2040 must be reliably soldered to ground for both electrical stability and thermal dissipation.
3. **USB Cable Quality:** Always use a data-capable USB-C cable (some phone charging cables lack USB 2.0 D+/D- lines).

---

## 📜 Credits & Acknowledgments

- **[Raspberry Pi Foundation](https://www.raspberrypi.com/)** for the RP2040 microcontroller and hardware design reference guidelines.
- **[Hack Club](https://hackclub.com/) & [Hack Club Forge](https://forge.hackclub.com/projects/1745)** for community support and grant funding.
- **[KiCad EDA](https://www.kicad.org/)** open-source electronic design automation suite.

---

## 📄 License

This hardware project is open-source under the MIT / CERN Open Hardware License. Feel free to clone, modify, and produce your own boards!