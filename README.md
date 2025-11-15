# MONOLITH-01

**The laptop that opens for you**

A custom ARM laptop built from boredom during winter break. Frosted stainless steel speaker panels, mechanical ortholinear keyboard, 2.5K display, and a custom carrier board for the CM3588.

![Build Status](https://img.shields.io/badge/build-in%20progress-orange)
![License](https://img.shields.io/badge/license-CERN--OHL--S%20v2-blue)
![Cost](https://img.shields.io/badge/cost-~€1000+-purple)

---

## Why This Exists

Boredom is underrated. Most interesting projects start because someone had nothing better to do and thought "what if?"

This laptop exists because I couldn't find one that checked all the boxes: mechanical keyboard that's actually mechanical (not membrane with fancy keycaps), proper aspect ratio for productivity, ARM architecture for the challenge, and something that didn't look like every other laptop. Winter break lasted too long, I had access to a makerspace, and here we are.

**The butterfly effect of boredom**: Free time leads to Wikipedia rabbit holes about ARM processors leads to "I wonder if I could run Linux on this" leads to KiCad tutorials at 2am leads to a functional custom laptop four months later.

---

# Design Philosophy

### Keyboard

The Planck is a 47-key ortholinear layout where every key sits in a perfect grid. No staggered rows, less finger travel, fully programmable with QMK. Hot-swap sockets mean you can try different switches without soldering.

### Speakers

The Utah monolith appeared in the desert in 2020. A perfect metal rectangle with no explanation. That's the aesthetic here: frosted stainless steel panels with no visible perforations from the front. Sound passes through micro-holes on the back side. #4 brushed finish gives the metallic look without showing every fingerprint.

### Display

13.3 inches at 2560×1600 in 16:10. More vertical space than 16:9 for code and documents. Matte finish because glare is the enemy.

### Carrier Board?

Designing a custom carrier board for the CM3588 means full control over ports, power delivery, and signal routing. 5-layer PCB with matte black solder mask. JLCPCB's assembly service handles the tiny surface-mount components. The CM3588 plugs in via SO-DIMM socket, so theoretically upgradeable if future modules use the same form factor.

### Chassis?

4mm aluminum plates mean zero flex. Matte black anodizing for durability. All screws exposed, no hidden clips, no adhesive. If it breaks, you can fix it. Framework hinge because there's no reason to reinvent what works.

## Why ARM?

ARM is efficient. The RK3588 sips power compared to x86 mobile chips. 8-15 hours of battery life with a 103Wh pack. Most tasks (web, coding, media) work natively. Games need FEX-Emu to translate x86 to ARM64, but Valve is actively developing it. Performance improves every month.

---

## How It Works?

### Power

USB-C PD negotiates 20V at 65W. Buck converters step down to 12V (display), 5V (USB, CM3588), and 3.3V (logic). The BMS handles charging, cell balancing, and seamless switching between wall power and battery.

### Thermal

Copper heatsink with dual heatpipes spreads heat to the aluminum chassis. The entire bottom plate acts as a passive heatsink. Normal use stays cool without a fan. Heavy workloads might benefit from an optional 40mm fan.

### Gaming

FEX-Emu translates x86 to ARM64 in real-time. 10-20% overhead. Light games (Minecraft, indie titles, older AAA) run well. Native ARM games and emulators run at full speed. Valve's investment means compatibility improves monthly.

# The Build

### Motherboard

Custom 5-layer PCB designed in KiCad. Power management, dual M.2 NVMe, eDP display, USB 3.0, I2S audio, I2C peripherals. Matte black solder mask with ENIG finish. JLCPCB assembly service handles SMT components.

### Chassis

6061-T6 aluminum, CNC milled. 4mm top/bottom plates, 3mm keyboard deck. Bead blasted, then matte black Type II anodized. Speaker panels are 304 stainless with #4 brushed finish, laser cut and perforated.

### Assembly

PCB mounts with standoffs. Batteries in front tray. Heatsink attaches to CM3588 and contacts bottom plate. Display screws into lid, eDP cable through hinge. Planck keyboard and Framework trackpad mount with screws. Speaker panels clip in from inside.

---

## What It Cost

Total: **€1,000+** (€920-950 with January sales)

**Major components:**
- CM3588 Plus 16GB: €133
- Custom PCB + assembly: €200
- Drop Planck V7: €120
- Display panel: €95
- Aluminum + anodizing: €100
- Framework trackpad: €55

---

## Specifications

### Computing
- **SoC**: Rockchip RK3588 (4× A76 @ 2.4GHz, 4× A55 @ 1.8GHz)
- **Module**: FriendlyElec CM3588 Plus
- **RAM**: 16GB LPDDR4X-4224
- **Storage**: 256GB NVMe M.2 2280
- **GPU**: Mali-G610 MP4 (Panfrost, Vulkan 1.3)
- **NPU**: 6 TOPS

### Display
- **Panel**: BOE B133QAN03.2
- **Size**: 13.3" diagonal
- **Resolution**: 2560×1600 (16:10)
- **Refresh**: 60Hz
- **Surface**: Matte anti-glare
- **Interface**: eDP 40-pin

### Input
- **Keyboard**: Drop Planck V7 (47-key ortho, Cherry MX hot-swap)
- **Keycaps**: Blank PBT (DSA/XDA)
- **Trackpad**: Framework touchpad (115×76.6mm)

### Audio
- **Speakers**: 2× 3W 4Ω drivers
- **Enclosure**: 304SS panels, #4 brushed
- **Perforation**: 0.5mm micro-holes (back only)

### Power
- **Battery**: 4× Samsung 18650-35E (103.6Wh)
- **Config**: 2S2P
- **BMS**: 4S 30A with balance
- **Charging**: USB-C PD 65W
- **Runtime**: 8-15 hours

### Chassis
- **Material**: 6061-T6 aluminum
- **Thickness**: 4mm (top/bottom), 3mm (deck)
- **Finish**: Type II anodizing, matte black
- **Dimensions**: 305×230×42mm
- **Weight**: ~2.0kg

### Connectivity
- **Ports**: 2× USB-C, 2× USB-A 3.0, HDMI 2.0, 3.5mm
- **Wireless**: Wi-Fi 6, Bluetooth 5.2
- **Expansion**: Dual M.2 slots

### Software
- **OS**: Ubuntu 24.04 LTS ARM64
- **Bootloader**: U-Boot
- **Kernel**: Linux 6.8+
- **Firmware**: QMK (keyboard)
- **Gaming**: FEX-Emu

---

## Performance

### CPU
Geekbench 5: ~850 single-core, ~3200 multi-core. Comparable to older Intel i5 or mid-range Ryzen mobile.

### Gaming
- **Minecraft Java**: 60-90 FPS @ 1080p
- **Indie games**: 60 FPS
- **Older AAA**: 45-60 FPS
- **Emulation**: Full speed (PS1, N64, GBA, DS)

### Battery
- **Light**: 12-15 hours
- **Medium**: 8-10 hours
- **Heavy**: 5-7 hours

---

## Repository Structure
```
MONOLITH-01/
├─ hardware/
│  ├─ carrier-pcb/         # KiCad project files
│  ├─ chassis/             # OnShape link + STEP exports
│  └─ speaker-panels/      # DXF for laser cutting
├─ firmware/
│  └─ keyboard/            # QMK configuration
├─ software/
│  ├─ ubuntu-setup/        # Installation scripts
│  └─ fex-emu-config/      # Gaming setup
├─ docs/
│  ├─ BOM.md              # Complete bill of materials
│  └─ learning.md         # Resources used
└─ README.md              # This file
```

---

## Credits

- **FriendlyElec** - CM3588 module
- **Framework** - Touchpad and repairability philosophy
- **Drop/OLKB** - Planck keyboard
- **Valve** - FEX-Emu development

---

## License

**Hardware**: CERN-OHL-S v2  
**Software**: GPL-3.0  
**Documentation**: CC BY-SA 4.0

---

**MONOLITH-01**: What happens when winter break lasts too long and you have access to a makerspace.

Built between December 2025 and March 2026.

---
