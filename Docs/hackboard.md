v1.0 required a "hack board" feedthrough to compensante for the TXB0108s'
inability to overcome the 10k pull-up resistors on the data bus. The
hack board was 3 40-pin male IDC connectors, 2 74HC245s, decoupling
capacitors, and a whole lot of wire wrap.

The following notes outline how I worked out what signals would be used
for those '245s to make everything work. Everything on the hack board
is referenced to Vcc=5V.

-jst 2018.09.15

B = SRAM
A = SY99

DIR = /OE
  /OE low  == B->A == reading from SRAM
  /OE high == A->B == writing to SRAM

/OE = /IC? Just tie low for now on this board

WW In D -> WW A terms on '245
WW In D -> solder terms on parallel output jack
WW Out D -> solder terms on my board jack

