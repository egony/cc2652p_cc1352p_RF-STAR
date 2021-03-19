# Zigbee Coordinator Firmware for RF-STAR RF-BM-2652P2 module (cc2652p chip)

## Firmware description:

Based on [Koenkk](https://github.com/Koenkk/Z-Stack-firmware/blob/master/coordinator/Z-Stack_3.x.0/firmware.patch) patches for Z-Stack_3.x.0.

### Changes from original firmware:
- Built for CC2652P1F chip variant (not for CC1352P1F).
- Default TX power: 20dBm. 
- LEDs are supported

### TX power ajust

Power can be adjusted in zigbee2mqtt config:

    experimental:
      transmit_power: 5

Available TX power values: -20, -18, -15, -12, -10, -9, -6, -5, -3, 0, 1..5, 14..20

### LEDs description
- Green (DIO7) turns ON when the network is running, blinking when joining enable
- Red (DIO6) flashed when APS frame received
- When stick restarted - both double blinking

Leds can be turned OFF by zigbee2mqtt config, but on March 2021 you need to modify file zStackAdapter.js:

    supportsLED() {
        return __awaiter(this, void 0, void 0, function* () {
          return true; //this.version.product !== tstype_1.ZnpVersion.zStack3x0; // <---- change like this
        });

### Buttons description
- Flash button on DIO15 used for bootloader activation (for firmware update)
- Reset button - you guess what it do.

### Notes

Coordinator backup from 2538/2652/1352 can be loaded back into another 2538/2652/1352, but into CLEAN (never used with zigbee2mqtt) chip only.
You can clear chip with zigbee2mqtt script **scripts\zStackEraseAllNvMem.js**

### Sources

As I know, sharing source codes prohibited by TI, so there is no sources here. And I can't made patches because they will include code. But you now what to do ;)

---

## Changelog:

### 2021-03-20

- LEDs now shows some events - reboot, network startup, join, data recieved
- LEDs now can be turned OFF by zigbee2mqtt config (require modifyed file zStackAdapter.js)

### 2021-02-10

- SDK 4.40.00.44

### 2020-09-21

- Initial release.
- SDK 4.20.01.04
- LEDs are supported
