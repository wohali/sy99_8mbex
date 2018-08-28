ideas
=====
1. Tie `/msbw`, `/lsbw`, `/OE`, `/IC` all high, `A0-A21` high
    * `LB#` low, `UB#` low, `WE#` high, `OE#` high
    * therefore output disabled / high-Z
    * can test transcievers on the way in

        * all transcievers look OK, unless they are bridged and stuck high.
            * D0, A16 needed resoldering, fixed
        * Should check all low next, can be with next test (for address lines anyway)

1. Tie `/msbw`, `/lsbw` high, `/OE` low, `/IC` high, `A0-A21` whatever
    * `LB#` low, `UB#` low, `WE#` high, `OE#` low
    * therefore `DQ0-DQ15` all active outputs on SRAM
    * can check data transciever for accuracy

1. try putting a few values into the SRAM, then read them back out
    * all zeroes
    * all ones
    * 0101010101010101
    * 1010101010101010
    * wire wrap on a 40 pin header with some pins removed is probably easiest
    * or use the top header, a 40-pin ribbon cable and some alligator clips to short values together
1. if this works, try some different address ranges
1. if you can get this far but it still fails, then go for the saleae
    * root problem: TXB0108 can't overcome the 10k pullup on the data lines on DM2

saleae signals to monitor (16)
==============================
* D0:D3
    * plus D0 on the "other side" of IC261/IC264 on DM2
* A0:A3
* A20, A21
* A23 (acts as /CE)
* /OE
* MSBW, LSBW
* CLK of course

test harness
============
freeSoC explorer based board
* LCD output
* 4 buttons: Addr+, Addr-, Data pattern, Write
* Validation mode:
    * Writes to SRAM with timing as declared
    * Reads from SRAM with timing as declared
    * If mismatch, write the failed pair to USB UART
    * Update display every 1s

