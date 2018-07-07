# QLA
Design files for Quad Linear Amplifier (QLA) board

* `QLA.PrjPCB`: Altium Designer project file
* `Snn.SchDoc`: schematics (Altium Designer format)
* `Snn.Harness`: signal harnesses (Altium Designer format)
* `AMP.PcbDoc`: PCB layout (Altium Designer format)
* `QLA-Schematics.pdf`: PDF of schematics
* `QLA-BOM.xls`: Bill of Materials (Microsoft Excel format)
* `QLA-HeatSink.pdf`: PDF of heat sink drawing
* `QLA-PCB-Fabrication.zip`: PCB fabrication (Gerber) files
* `QLA-Assembly.zip`: PCB assembly files (e.g., paste masks, pick-and-place)
 
## Release Notes

* Rev 1.1: Build #0 (5 board pilot run)
* Rev 1.2: Build #1 (44 boards)
  * Deleted trace from Q15A (MOSFET) to U39B (OPA549) to avoid glitches at power-up (on all 4 channels)
  * Added J11 to enable connection to remote LED panel
* Rev 1.3 (PCB silkscreen is Rev 1.2): Build #2 (68 boards), Build #3 (72 boards), Build #4 (80 boards)
  * Changed relay (U31) from +12V to +5V to avoid rework needed to bring external +12V to board
  * Fixed silkscreen for Pot2 and Pot3 test points (they were swapped)
  * Changed R52 to 0 Ohms (Rev 1.1 and 1.2 boards were reworked accordingly)
  * Added screwlocks (Female, 4-40, 0.185") to DB9 connector
  * Design files indicate Rev 1.3, but manufactured boards show Rev 1.2; boards can be distinguished by looking at relay (U31)
* Rev 1.4: Build #5 (92 boards)
  * Changed digital outputs from open-drain MOSFETs to bi-directional bus transceivers (74LVC2T45) with 5V output; direction controlled by FPGA IO1-5 and IO1-6. Proper operation requires FPGA Firmware Rev 5+
  * Added feedback of motor voltage fault (from LT4356) on FPGA IO1-7
  * Grounded heatsink on PCB
  * Added plated slots for soldering 68-pin connector tabs
  * Moved Q13, Q14 and updated PCB pads to facilitate assembly
* Rev 1.4a: Build #6 (75 boards)
  * Increased maximum motor supply voltage from ~50.2V to ~52.7V
    * Changed R33, R34 to raise LT4356 maximum voltage from ~51.25V to ~52.7V
    * Changed R27, R28 to set MV_GOOD window comparator thresholds to 11.0V and 55.2V (which should never be reached due to 52.7V limit on LT4356)
  * Added transorb SMAJ64CA on back side of connector J5, between pins 2 and 3, to limit flyback voltages on motor power supply (especially with 48V supply)
