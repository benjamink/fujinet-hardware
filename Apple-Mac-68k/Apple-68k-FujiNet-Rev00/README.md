# Apple 68k FujiNet Rev00 (ESP32-S3)

Prototype of Rev0 with the ESP32-DevKitC replaced by an ESP32-S3-DevKitC-1 (N16R8) style board,
such as the dual USB-C "HW-678" clones. Not yet built or tested.

- The board is 15.24mm longer at the USB edge so the longer S3 devkit's USB end sits at the edge,
  as on Rev0. The Pico (with D3, JP1 and R1-R3 under it), S1, C2 and the bottom mounting holes
  moved down with it, so both USB ports stay on that edge; the case needs the same change.
- U2's right-hand header row has holes at both 22.86mm (Espressif DevKitC-1) and 25.4mm (most
  clones) spacing. Solder the socket into whichever row matches your board.
- RN1 moved to clear the 22.86mm row. Everything else is where it was on Rev0.
- Mac signals, the Pico and the microSD socket are unchanged. The GPIO assignment is new:

| Signal | GPIO | | Signal | GPIO |
|---|---|---|---|---|
| SPI_CS | 4 | | WR_DATA | 1 |
| SPI_MOSI | 5 | | WREQ | 2 |
| SPI_CLK | 6 | | ENBL2 | 42 |
| SPI_MISO | 7 | | HDSEL | 41 |
| SD_CD | 15 | | RMT_FROM_ESP | 40 |
| BUTTON_A | 16 | | PICO_RX_TO_ESP (ESP TX) | 39 |
| LED_WIFI | 17 | | PICO_TX_TO_ESP (ESP RX) | 21 |
| BUS_LED | 18 | | SAFE_RESET | 8 |

GPIO 0, 3, 45 and 46 (strapping), 19/20 (USB), 43/44 (UART0), 35-37 (octal PSRAM) and 38/48
(RGB LED on most devkits) are left unconnected.

The ESP32-S3-DevKitC symbol and footprint in `lib/` are derived from Espressif's
[kicad-libraries](https://github.com/espressif/kicad-libraries) (CC-BY-SA 4.0).
