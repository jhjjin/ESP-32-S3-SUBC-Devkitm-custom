# ⚡ ESP32-S3 USB-C DevkitM Custom Board  
Custom **ESP32-S3 (ESP32-S3-MINI-1-N8)** development board designed from scratch in **Altium Designer 25.8.1**, featuring USB-C connectivity, FT231X UART bridge, ESD protection, and a 4-layer impedance-controlled PCB verified for **JLCPCB** manufacturing standards.  

---

## 🧩 Overview
```
> A fully custom ESP32-S3-MINI-1-N8 dev board built as a learning and portfolio project.  
> Designed and validated for manufacturability, signal integrity, and professional layout discipline.
```
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
| USB-UART | FT231XQ-R | FTDI | – |
| ESD Protection | AQ3045-01ETG | Littelfuse | – |
| Regulator | TI LDO (3.3 V) | Texas Instruments | – |
| LED | RC0402FR-071KL (1 kΩ) | Yageo | – |
| Cap | CL05B104KB54PNC (100 nF) | Samsung | – |
| Cap | CL05A475MO5NUNC (4.7 µF) | Samsung | – |
| Jumper | FTS-103-01-F-S / FTS-102-01-F-S | Samtec | – |

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
  <img src="./docs/images/Layer.PNG" width="85%" alt="PCB Layout Overview">
</p>

| 3D Front | 3D Back |
|:---------:|:--------:|
| <img src="./docs/images/PCB%203D%20Front.PNG" width="95%" alt="3D Front View"> | <img src="./docs/images/PCB%203D%20Back.PNG" width="95%" alt="3D Back View"> |

> **Figure:** PCB layout (Layer) and 3D render previews for the custom ESP32-S3 USB-C DevkitM board.

---
## 🧾 Output & Fabrication
```

Gerber / NC Drill: inches, verified in ViewMate

Layer sequence: L1:GTL, L2:G1, L3:GP1, L4:GBL

BOM: CSV includes LCSC + Manufacturer PN

Pick & Place: Center X/Y, Rotation, Layer, Footprint

PDFs: Top, Bottom, Schematic (A4 @100%)

DRC: All green — only silk/placement waivers noted

🏭 Fabricated for JLCPCB 4-Layer Standard Process
FR-4, Green/White, 1.6 mm, HASL (Lead), Full Probe Test
```
---
## 🧠 Learnings & Focus
```

Real-world PCB stackup and impedance control

Rule-based design approach (Component, Clearance, DiffPairs)

Synchronizing schematic ↔ PCB libraries

DRC-driven layout verification

Preparation of Gerber, BOM, Pick & Place, and PDF documentation
```
---
