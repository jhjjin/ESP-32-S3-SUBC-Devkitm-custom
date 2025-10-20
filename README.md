# ⚡ ESP32-S3 USB-C DevkitM Custom Board  
Custom **ESP32-S3 (ESP32-S3-MINI-1-N8)** development board designed from scratch in **Altium Designer 25.8.1**, featuring USB-C connectivity, FT231X UART bridge, ESD protection, and a 4-layer impedance-controlled PCB verified for **JLCPCB** manufacturing standards.  

---

## 🧩 Overview

- A fully custom ESP32-S3-MINI-1-N8 dev board built as a learning and portfolio project.  
- Designed and validated for manufacturability, signal integrity, and professional layout discipline.
--- 
Key specs:
- ✅ USB-C interface (Molex I/O connector)
- ✅ FTDI FT231XQ-R USB-UART bridge  
- ✅ Littelfuse AQ3045-01ETG (ESD/TVS Protection)
- ✅ Low-dropout regulator with ESR 20 µF input cap  
- ✅ Differential pair routing for USB 2.0  
- ✅ Variant setup for NF (DNP) parts  
- ✅ JLCPCB 4-Layer Stackup (JLC04161H-3313)

---

## 🛠️ Design Tools & Environment
| Tool | Version | Purpose |
|------|----------|----------|
| **Altium Designer** | 25.8.1 | Schematic, PCB, DRC |
| **ViewMate** | 11.14 | Gerber Verification |
| **SnapEDA / 3D ContentCentral** | – | STEP Models / Footprints |
| **JLCPCB Calculator** | – | Impedance Matching |

---

## 📐 PCB Stackup
| Layer | Type | Notes |
|-------|------|-------|
| **L1** | Signal (Top) | High-speed USB / MCU routing |
| **L2** | GND Plane | Solid ground reference |
| **L3** | Power Plane | +3V3 / +5V islands |
| **L4** | Signal (Bottom) | GPIO, UART, LED, test traces |

📏 **Stackup:** JLC04161H-3313 (1.6 mm FR-4)  
🎯 **USB 90 Ω diff / 50 Ω single** controlled impedance

---

## ⚙️ Main Components

| Function | Part | Supplier | LCSC Part No |
|-----------|------|-----------|---------------|
| MCU | ESP32-S3-MINI-1-N8 | ESPRESSIF | **C2913206** |
| USB-UART | FT231XQ-R | FTDI | **C3212159** |
| ESD Protection | AQ3045-01ETG | Littelfuse | **C3710326** |
| Regulator | TL1963A-33DCYR (3.3 V LDO) | Texas Instruments | **C1812626** |
| LED (Green) | VLMG1500-GS08 | Vishay | **C5111404** |
| LED (Red) | VLMS1500-GS08 | Vishay | **C5111370** |
| Cap (100 nF, 50 V) | CL05B104KB54PNC | Samsung | **C307331** |
| Cap (4.7 µF, 16 V) | CL05A475MO5NUNC | Samsung | **C318563** |
| Resistor (1 kΩ) | RC0402FR-071KL | Yageo | **C106023** |
| Resistor (4.7 kΩ) | RC0402FR-074K7L | Yageo | **C105871** |
| Resistor (5.1 kΩ) | RC0402FR-075K1L | Yageo | **C1447745** |
| Resistor (10 kΩ) | RC0402FR-0710KL | Yageo | **C1444807** |
| Jumper Header (2-pin) | FTS-102-01-F-S | Samtec | **C6045317** |
| Jumper Header (3-pin) | FTS-103-01-F-S | Samtec | **C3333578** |
| Shunt | M50-1920005 | Harwin | **C6985646** |
| USB-C Connector | 217179-0001 | Molex | **C3197684** |
| Transistor | SS8050-G | Comchip | **C21406** |
| Diode (TVS) | AQ3045-01ETG | Littelfuse | **C3710326** |

---

## 🧭 Schematic Overview
```
USB-C (Power / Data)
     │
[FT231X UART Bridge]
     │
ESP32-S3-MINI-1-N8 ←→ Boot / Reset / LEDs / Headers
     │
[LDO Regulator]
     │
+3V3 / +5V
```
---

---

## 🔍 Build Notes & Troubleshooting

### ⚡ Common Design Challenges
| Issue | Cause | Fix |
|--------|--------|-----|
| GND recognized as +3V3 | Power port misconnection | Disconnect and redraw from `GND` port |
| FTDI clearance too tight | Dense routing | Define `Room('FTDI')` and set clearance 6 mil |
| USB diff pair warning | Width/gap mismatch | Apply `DIFF90` rule (6.03 mil / 8 mil) |
| “Footprint not found” (J6) | Library mismatch | Re-link footprint and `Design ▸ Update PCB` |
| Silk-to-mask errors | Fabrication tolerance | Set `Silk to Mask = 5 mil` per JLC spec |
| 3D misalignment | STEP origin offset | `3D Body ▸ Align Face with Body` → `Set Reference Center` |

---

### 🧱 PCB Layout Highlights
- **Via:** Ø 24 mil / hole 12 mil  
- **USB diff pairs:** 6.03 mil width, 8 mil spacing  
- **Power tracks:** 15 mil width  
- **GND stitching vias:** around USB and RF areas  
- **Polygon pour:** direct connect for +3V3, thermal for GND  

 
## 🖼️ Hardware Preview

<p align="center">
  <img src="https://github.com/jhjjin/ESP-32-S3-SUBC-Devkitm-custom/blob/main/Layer.PNG?raw=true" width="85%" alt="PCB Layout Overview">
</p>

| 3D Front | 3D Back |
|:---------:|:--------:|
| <img src="https://github.com/jhjjin/ESP-32-S3-SUBC-Devkitm-custom/blob/main/PCB%203D%20Front.PNG?raw=true" width="95%" alt="3D Front View"> | <img src="https://github.com/jhjjin/ESP-32-S3-SUBC-Devkitm-custom/blob/main/PCB%203D%20Back.PNG?raw=true" width="95%" alt="3D Back View"> |

> **Figure:** PCB layout (Layer) and 3D render previews for the custom ESP32-S3 USB-C DevkitM board.


---
---

## 📦 Fabrication Outputs

The project includes full manufacturing and assembly documentation for **JLCPCB** and other PCB assembly vendors.

### 🧾 Bill of Materials (BOM)
| Field | Example |
|:------|:--------|
| **Component Count** | 38 unique parts (Samsung, Yageo, FTDI, Espressif, TI, etc.) |
| **Main ICs** | ESP32-S3-MINI-1-N8, FT231XQ-R, TL1963A-33DCYR |
| **Passive Parts** | 0402 Capacitors & Resistors (Yageo / Samsung) |
| **ESD / Protection** | Littelfuse AQ3045-01ETG |
| **Connectors** | Molex USB-C (217179-0001), Samtec Headers (FTS-103-01-F-S / FTS-102-01-F-S) |
| **LEDs** | Vishay VLMG1500-GS08 (Green), VLMS1500-GS08 (Red) |
| **Supplier Integration** | LCSC + DigiKey references with cross-checked MPNs |

🧩 The BOM is exported directly from **Altium Designer 25.8.1**, containing:
- Description, Designator, Footprint, Quantity, Manufacturer, MPN, LCSC / DigiKey number  
- All capacitors and resistors use **0402 metric footprint**  
- Variant configuration for **NF (Not Fitted)** parts included  



---

### 📍 Pick & Place (Component Position)
| Field | Example Data |
|:------|:--------------|
| **Coordinates** | X/Y in mils (Altium standard) |
| **Rotation** | 0°, 90°, 180°, 270° |
| **Layers** | TopLayer / BottomLayer |
| **Included Fields** | Designator, Comment, Layer, Footprint, Center-X, Center-Y, Rotation, Description |



---
## 🧠 Learnings & Focus


- Real-world PCB stackup and impedance control

- Rule-based design approach (Component, Clearance, DiffPairs)

- Synchronizing schematic ↔ PCB libraries

- DRC-driven layout verification

- Preparation of Gerber, BOM, Pick & Place, and PDF documentation

---
