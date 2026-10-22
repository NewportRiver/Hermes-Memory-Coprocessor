# ROMRAM source acquisition and hardware notes

Source: https://dmitry.gr/?proj=10.+RomRam&r=06.+Thoughts
Original archive: https://dmitry.gr/images/romram.zip
Hardware reference (not custom board schematic): https://datasheets.raspberrypi.com/rp2040/hardware_design_with_rp2040.pdf

## Verified from original author
- RP2040 SSI/XIP memory mapping with 8 MB QSPI RAM.
- Flash-to-RAM boot uses two OR gates, a NAND gate configured as inverter, and two resistors to select flash or RAM chip-select.
- Author describes using an I2C IO expander for RAM/nROM control due to a reset-related issue.
- MPU write protection triggers HardFault; handler emulates ARMv6-M stores and issues SSI writes; XIP cache must be invalidated appropriately.
- Author reports 36 Mbit/s memcpy write throughput at stock clocks and ~363 cycles for a simple word store.
- Source download is described as second-stage loader and HardFault handler under BSD-2-Clause.

## Retrieval status (2026-10-22)
The author's ZIP URL was confirmed in the original write-up, but downloading ZIP bytes was not possible from the current environment. **The archive, any schematic, and BOM have NOT been imported or verified.** Do not fabricate schematics or component part numbers.

## Next acquisition step
From a machine with internet access, download `romram.zip` from the author's website. Before committing any files:
1. List archive contents and inspect README, source headers and license.
2. Confirm whether there are schematics, PCB files, BOM, or only firmware.
3. Preserve BSD-2-Clause license and attribution for any imported code.
4. Keep original files in `third_party/romram/` with provenance, separate from our designs.
5. Document exact chip models, voltages, pin assignments and electrical limits from original source.
6. Commit only materials permitted by their license.

## Our hardware design
The RP2040 reference schematic is **not** the author's ROMRAM custom schematic. Design an independently documented companion board after verifying source hardware, with a separate USB/network API rather than claiming direct Galaxy A37 RAM expansion.
