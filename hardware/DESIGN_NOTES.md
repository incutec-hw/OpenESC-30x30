# Design Notes

Engineering notes mirrored from the on-canvas comments in the KiCad schematic
(`4in1.kicad_sch`, `ESC.kicad_sch`). This file is the human-readable copy of the
design rationale annotated directly on the sheets — keep the two in sync.

> This is the **30×30** OpenESC. The
> [OpenESC_20X20](https://github.com/incutec-hw/OpenESC_20X20) (20×20 mm) shares
> this design and carries the same notes; the two differ only in board/mounting
> size and a few power-stage parts (MOSFET, TVS, shunt count).

---

## Main sheet (`4in1.kicad_sch`)

**Topology:** +BATT input, TVS clamp, buck + LDO power, board-level current sense, 8-pin connector.

### Connector / telemetry
- **No telemetry signal pin** — telemetry is handled by the **extended DShot
  protocol** (bidirectional, over the motor signal lines). Connector pin 4 is
  therefore intentionally unconnected.

### Input protection
- 3× **SMBJ24A** TVS on +BATT. The SMBJ24A means there will be some leakage at a
  fully charged 6S pack (25.2 V), but voltage clamping is improved too — tradeoff
  being monitored.

### Buck (gate-drive rail)
- **LMR54406DBVR**: 4–36 V input, can handle 50 V spikes (8S support TBD).
- 1.1 MHz switching, 0.6 A — plenty for gate driving.
- FTC160808S4R7MBCA 4.7 µH inductor. FB divider 115k / 10k, Vref 0.8 V → **10.0 V** rail.

### Current sense
- Board-level high-side: 0.2 mΩ shunt × 100 V/V (INA186A3) gain.
- **Two parallel shunts = 0.1 mΩ → 10 mV/A → ~330 A** full-scale at 3.3 V ADC.

### Decoupling
- Total array of 8×6 + 2 = **50 decoupling caps**. At 25 V DC bias each cap derates
  to only ~1.5–2 µF, so 75–100 µF total but very low ESL.

---

## Per-channel ESC (`ESC.kicad_sch`)

**Topology:** a single ESC channel, duplicated 4×. One AT32 MCU + one NSG2065Q gate
driver + 6 MOSFETs (low and high side per phase).

- **Microcontroller:** AT32 (AT32F421G8U7). Flashed via SWC.
- **Gate driver:** NSG2065Q — gate driver has an integrated diode.
- **MOSFETs:** low and high side for each phase. **XRS280N03C selected**
  (C50314140, 30 V / 280 A / 0.5 mΩ, PDFN-8L 5×6, drop-in footprint) as the
  next-gen part — current build still populates SP40N01GHNK.
- **Bootstrap capacitors** for high-side N-MOS switching.
- **BEMF feedback network** for sensorless commutation.
- **LPF on VDDA** (MCU analog supply).
