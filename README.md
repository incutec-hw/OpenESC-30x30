# Open 4-in-1 AM32 ESC — 30x30

30x30mm mounting pattern variant of the [Open 4-in-1 AM32 ESC](https://github.com/stan-so/4in1ESC). Designed for higher current handling with more copper area and upgraded components. Runs [AM32](https://github.com/AlkaMotors/AM32-MultiRotor-ESC-firmware) firmware, works with Betaflight over DShot. Designed in KiCad 9, ready to order from JLCPCB.

## Specs

| Parameter | Value |
|---|---|
| Firmware | AM32 |
| Input voltage | 3-6S LiPo (11.1-25.2V) |
| MCU | AT32F421G8U7 (ARM Cortex-M4, 120MHz) |
| Gate driver | **NSG20652Q** (3-phase, C41414479) |
| MOSFETs | **SP40N01GHNK** (TBD — evaluate for higher current) |
| Current sensing | INA186A3IDCKR (C2058245) + 0.2mOhm shunt |
| Protocol | DShot (Betaflight compatible) |
| Power supply | LMR51420XDDCR buck (C5246146) + TLV76733DRVR LDO (C2848334) |
| Connector | JST SM08B-SRSS-TB (C160407) — Betaflight 8-pin standard |
| Ferrite bead | BLM03PX121SN1D (C525479) 120R 0201 |
| PCB | **4-layer, 30x30mm**, designed for JLCPCB PCBA |

## Hardware Changes vs 20x20 Variant

| Component | 20x20 | 30x30 | Notes |
|-----------|-------|-------|-------|
| **Gate Driver** | NSG2065Q (C41414478) | **NSG20652Q (C41414479)** | Different pinout — NOT pin-compatible. Adds SD pin. |
| **MOSFETs** | SP40N03GNJ (C22466709) | **SP40N01GHNK** (TBD) | Evaluate for higher current |
| **Board Size** | 20x20mm, 6-layer | **30x30mm, 4-layer** | More copper area for thermals |
| **Buck Converter** | LMR51420XDDCR (C5246146) | Same | |
| **LDO** | TLV76733DRVR (C2848334) | Same | 3.3V |
| **Current Sense** | INA186A3IDCKR (C2058245) | Same | SC-70-6, 100V/V |
| **Connector** | JST SM08B-SRSS-TB (C160407) | Same | Betaflight 8-pin standard |
| **Ferrite Bead** | BLM03PX121SN1D (C525479) | Same | 120R 0201 |

## Key Notes — NSG20652Q vs NSG2065Q

- Completely different pinout (only 3 of 24 pins match) — needs full PCB layout from scratch
- Adds SD (shutdown) pin on pin 8
- Slightly different gate drive: 1A/1.4A source/sink vs 1.5A/1.2A
- VCC min is 5V (vs 8V for NSG2065Q)

## Project Structure

```
4in1ESC-30x30.kicad_sch     Main schematic (power, sensing, connector)
ESC.kicad_sch                Single ESC channel (used 4x)
4in1ESC-30x30.pretty/        Custom footprints
4in1ESC-30x30.3dshapes/      3D models (STEP files)
components.kicad_sym          Custom symbols
```

## Status

- [ ] Import NSG20652Q symbol and footprint
- [ ] Import SP40N01GHNK symbol and footprint
- [ ] Update schematic for NSG20652Q pinout (SD pin, different pin mapping)
- [ ] PCB layout (30x30mm, 4-layer)
- [ ] Thermal analysis
- [ ] JLCPCB fabrication files

## License

Licensed under [CERN-OHL-S-2.0](https://ohwr.org/cern_ohl_s_v2.txt). You can use, modify, and sell this design, but any modifications must also be open-sourced under the same license.
