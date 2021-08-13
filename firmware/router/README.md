# Zigbee Router Firmware for RF-STAR RF-BM-2652P2 module (cc2652p chip)

## Firmware description

Based on [Koenkk](https://github.com/Koenkk/Z-Stack-firmware/blob/master/router/Z-Stack_3.x.0/firmware.patch) patches for Z-Stack_3.x.0.
Please read description of [original firmware](https://github.com/Koenkk/Z-Stack-firmware/blob/master/router/Z-Stack_3.x.0/bin/README.md)

### Changes from original firmware
- SDK 5.10.00.48
- Built for CC2652P1F chip variant (not for CC1352P1F).
- Default TX power: 20dBm.
- LEDs are supported, but not used

### LEDs description
When device restarted - both double blinking.

### Pairing
After reflashing the router will automatically pair.

### Facrory reset
- To factory reset single press the any button on your device (except reset button of course).
- If your device have no buttons, just reflash it again.

### Sources

As I know, sharing source codes prohibited by TI, so there is no sources here. And I can't made patches because they will include code. But you now what to do ;)

---

## Changelog (except KoenKK's patches update)

### 2021-08-12

- Initial release.
- SDK 5.10.00.48
- Built for CC2652P1F chip variant (not for CC1352P1F).
- Default TX power: 20dBm. 
- LEDs are supported, but not used for now 

