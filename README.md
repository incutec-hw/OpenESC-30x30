# 4in1 ESC 30x30

30x30mm mounting pattern variant of the Open 4-in-1 AM32 ESC.

## Hardware Changes vs 20x20 Variant

| Component | 20x20 | 30x30 | Notes |
|-----------|-------|-------|-------|
| **Gate Driver** | NSG2065Q (C41414478) | **NSG20652Q (C41414479)** | Different pinout - NOT pin-compatible. Adds SD pin. 3,766 stock. |
| **MOSFETs** | SP40N03GNJ (C22466709) | **SP40N01GHNK** (TBD) | Evaluate for higher current |
| **Board Size** | 20x20mm | **30x30mm** | More copper area for thermals |
| **Buck Converter** | LMR51420XDDCR (C5246146) | Same | Pin-compatible, 5k+ stock |
| **LDO** | TLV76733DRVR (C2848334) | Same | 3.3V LDO |
| **Current Sense** | INA186A3IDCKR (C2058245) | Same | SC-70-6, 100V/V |
| **Connector** | JST SM08B-SRSS-TB | Same | Betaflight 8-pin standard |
| **Inductor** | 470nH 0603 (TBD) | Same | Need stable 1608 source |
| **Ferrite Bead** | BLM03PX121SN1D (C525479) | Same | 120R 0201, 76k stock |

## Key Notes

- NSG20652Q has completely different pinout from NSG2065Q (only 3 of 24 pins match)
- NSG20652Q adds SD (shutdown) pin on pin 8
- NSG20652Q has slightly different drive: 1A/1.4A source/sink vs 1.5A/1.2A
- NSG20652Q VCC min is 5V (vs 8V for NSG2065Q)
- Needs full PCB layout from scratch - cannot reuse 20x20 layout

## Status

- [ ] Import NSG20652Q symbol and footprint
- [ ] Import SP40N01GHNK symbol and footprint
- [ ] Design schematic
- [ ] PCB layout (30x30mm, 4-layer)
- [ ] Thermal analysis
- [ ] JLCPCB fabrication files

## License

CERN-OHL-P v2
