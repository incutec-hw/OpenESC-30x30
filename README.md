# Open 4-in-1 AM32 ESC — 30x30

30x30mm mounting pattern variant of the [Open 4-in-1 AM32 ESC](https://github.com/Just4Stan/Open-4in1-AM32-ESC). Designed for higher current handling with more copper area and upgraded components. Runs [AM32](https://github.com/AlkaMotors/AM32-MultiRotor-ESC-firmware) firmware, works with Betaflight over DShot. Designed in KiCad 9.

## Specs

| Parameter | Value |
|---|---|
| Firmware | AM32 |
| Input voltage | 3-6S LiPo (11.1-25.2V) |
| MCU | AT32F421G8U7 (ARM Cortex-M4, 120MHz) |
| Gate driver | **NSG2065Q** (3-phase, FD6288Q-compatible) |
| MOSFETs | **SP40N01GHNK** N-CH 40V 120A PDFN-8L(5x6) |
| Current sensing | INA186A3IDCKR + 0.2mOhm shunt |
| Protocol | DShot (Betaflight compatible) |
| Power supply | LMR51420XDDCR buck + TLV76733DRVR LDO |
| Connector | JST SM08B-SRSS-TB — Betaflight 8-pin standard |
| Ferrite bead | BLM03PX121SN1D 120R 0201 |
| PCB | **6-layer, 30x30mm** mounting pattern, designed for JLCPCB PCBA |

## Hardware Changes vs 20x20 Variant

| Component | 20x20 | 30x30 | Notes |
|-----------|-------|-------|-------|
| **Gate Driver** | NSG2065Q (C41414478) | Same | FD6288Q-compatible — 7+ drop-in alternatives, 27k+ combined stock |
| **MOSFETs** | SP40N03GNJ (C22466709) | **SP40N01GHNK** (C22385416) | 40V 120A PDFN-8L(5x6), up from 75A PDFN-8L(3x3) |
| **Mounting Pattern** | 20x20mm, 6-layer | **30x30mm, 6-layer** | More copper area for thermals |
| **Buck Converter** | LMR51420XDDCR (C5246146) | Same | |
| **LDO** | TLV76733DRVR (C2848334) | Same | 3.3V |
| **Current Sense** | INA186A3IDCKR (C2058245) | Same | SC-70-6, 100V/V |
| **Connector** | JST SM08B-SRSS-TB (C160407) | Same | Betaflight 8-pin standard |
| **Ferrite Bead** | BLM03PX121SN1D (C525479) | Same | 120R 0201 |

## Alternative Gate Drivers

The NSG2065Q uses the FD6288Q pinout (QFN-24 4×4mm). These are drop-in replacements with zero PCB changes:

| Part | Manufacturer | LCSC | Stock | Price |
|------|-------------|------|-------|-------|
| NSG2065Q | Novosense | C41414478 | ~225 | $0.44 |
| 6288Q-MNS | Minos | C49424413 | 9,890 | $0.30 |
| SD6288Q | JSMSEMI | C44606223 | 5,045 | $0.31 |
| EG2124 | EG Micro | C2856308 | 3,821 | $0.23 |
| HL6288Q | HL | C50331902 | 3,272 | $0.19 |
| YC6288Q | YLPTEC | C54157432 | 2,946 | $0.42 |
| JSM6288Q | JSMSEMI | C19077370 | 1,989 | $0.46 |

See the [20x20 variant ALTERNATIVES.md](https://github.com/Just4Stan/Open-4in1-AM32-ESC) for full pinout table and detailed compatibility notes.

## Project Structure

```
4in1ESC-30x30.kicad_sch     Main schematic (power, sensing, connector)
ESC.kicad_sch                Single ESC channel (used 4x)
4in1ESC-30x30.pretty/        Custom footprints
4in1ESC-30x30.3dshapes/      3D models (STEP files)
components.kicad_sym          Custom symbols
```

## Status

- [x] Import SP40N01GHNK symbol and footprint
- [x] PCB layout (30x30mm, 6-layer)
- [ ] Order from JLCPCB
- [ ] Thermal analysis

## License

Licensed under [CERN-OHL-S-2.0](https://ohwr.org/cern_ohl_s_v2.txt). You can use, modify, and sell this design, but any modifications must also be open-sourced under the same license.
