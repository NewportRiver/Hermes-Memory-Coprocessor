# Original ROMRAM research references

## Primary source
- Original technical write-up: https://dmitry.gr/?proj=10.+RomRam&r=06.+Thoughts
- Original source ZIP (second-stage loader and HardFault handler): https://dmitry.gr/images/romram.zip
- Original coverage: https://www.hackster.io/news/dmitry-grinberg-s-romram-adds-8mb-of-external-ram-to-the-humble-raspberry-pi-rp2040-27f2d7363f10
- Raspberry Pi RP2040 hardware design and reference schematics: https://datasheets.raspberrypi.com/rp2040/hardware_design_with_rp2040.pdf

## Technical concepts to study
1. QSPI SRAM / PSRAM memory mapping via RP2040 SSI/XIP.
2. Flash-to-RAM boot and chip-select selection logic (two OR gates and inverter).
3. MPU write protection and HardFault-based store instruction emulation.
4. XIP cache invalidation and QSPI timing constraints.
5. Original measured ~36 Mbit/s memcpy-to-ROMRAM and ~363 cycles per simple word store (author's results, not Android benchmarks).

## Schematic status
The author's write-up describes the glue logic, and the official RP2040 hardware design guide includes reference schematics. The downloadable ROMRAM archive is described as source code; **do not assume it includes a complete ROMRAM PCB schematic or Gerber set** until the ZIP has been inspected. Do not claim the RP2040 reference schematic is the custom ROMRAM board.

## Provenance and licensing
Author: Dmitry Grinberg. Original ROMRAM code is stated to be BSD 2-clause licensed. Retain attribution and the original license text if importing code. Link to source rather than copying unknown schematic assets without verifying licensing.

## Relevance and limitations
ROMRAM extends memory *inside an RP2040 microcontroller*. It does not give a Samsung Galaxy A37 additional system RAM via USB-C. Our project can use its principles to study a dedicated memory coprocessor, but a practical Android companion should initially expose a network/API service.

## Retrieval checklist
- [ ] Download and inspect `romram.zip` in an isolated workspace
- [ ] Inventory source files and any schematics, PCB layouts, pinouts, BOM
- [ ] Verify license headers and hardware reuse terms
- [ ] Identify actual PSRAM chip and gate part numbers from original materials
- [ ] Document electrical voltage, timing, power and USB interface requirements
- [ ] Create original derivative block schematic only after validating pin assignments
