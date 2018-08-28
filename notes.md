Mappings for level translation
==============================
* A0-A15 (74)
* A16,17,18,19,20,21, 23(CE), /OE, /MSBW, /LSBW, /IC (74) +5 spare lines
* D0-D7 (TX)
* D8-D15 (TX)

Chip listing
============
* 2x TXB0108; 2X 74ALVC164245 (Level shifters) (optionally: use 2x SN74LVCH16T245DGGR )
* 1x AS6C6416-55TIN (64Mb SRAM)
* 1x BQ2205LYPWR (NVRAM controller)
* 1x AZ1117EH-3.3TRG1 (3v3 LDO regulator)
* 3x SN74LVC1G97DBVR (or DRL or DCK)
    * dbv - 3.05/1.75 (0.95mm spacing)
    * dck - 2.15/1.40 (0.65mm spacing)
    * drl - 1.7/1.3 (.5 mm spacing)

Connectors
==========
* IDC 40pin
* 2mm conn - 51004-1400 
    * https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20180720225620&SearchText=ph2.0
    * https://www.toby.co.uk/cable-wire-to-board/200mm-crimp-and-poke/ph200-valcon-2mm-pitch-vertical-wire-to-board-pcb-connector/

ASSUMPTIONS CHECKED
===================
* OK 74ALVC164245 - A bus is 3.3, B bus is 5, OE low, DIR low (B-> A)
* OK TXB0108PWR - OE is high, A bus is 3.3, B bus is 5
* OK Check if reset line can be used for CE2.
* OK BQ2205LY - Review the SBT line
* OK 74LVC1G97S - all the logic
* Everything related to RAM:
    * OK WE#
    * OK OE# (driven by 3V3 /OE)
    * OK LB#
    * OK UB#
    * OK BYTE# (always high)
    * OK CE#
    * OK CE2 (driven from /IC)

TODO
====
* Mounting hardware
   * foam-backed double-sided sticky tape?
   * Extend PCB to include screw hole?

ECOs in v1.0
=============
1. CE and CST swapped on J2, J4
1. fix silkscreen for LEDs, incorrect orientation
1. pullup for pin 16 battery mgmt chip, 3k3
1. ground unused outputs/inputs on transceiver chip U1
1. Pads for J4 are too small, make wide like J2 (or vice versa?)
1. add TP for Vram output from backup monitor chip
1. and maybe:
    1. add a reset button for pin 16 battery mgmt chip?
    1. add LED for bad battery? Need to check if this stays lit when on battery!
    1. increase current limiting resistors for the LEDs?
    1. look at some sort of connector for the 14-pin cable?
