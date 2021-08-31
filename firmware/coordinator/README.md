# Zigbee Coordinator Firmware for RF-STAR RF-BM-2652P2 module (cc2652p chip)

## Warning!!! Because of zigbee2mqtt 1.21 have broken LED support, see fixing details below.

## Firmware description

Based on [Koenkk](https://github.com/Koenkk/Z-Stack-firmware/blob/master/coordinator/Z-Stack_3.x.0/firmware.patch) patches for Z-Stack_3.x.0.

### Changes from original firmware
- SDK 5.20.00.52
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

Leds can be turned OFF/ON by zigbee2mqtt config.

Led support broken in zigbee2mqtt 1.21.0, so you should edit controller.js file like this:

    nano /opt/zigbee2mqtt/node_modules/zigbee-herdsman/dist/controller/controller.js
    
![](https://github.com/egony/cc2652p_E72-2G4M20S1E/blob/master/images/z2m_fix.png)

For firmware 2021-03-20 and earler find string

    this.supportsLED_ = !zStack3x0 || (zStack3x0 && parseInt(this.version.revision) >= 20210430);
    
and change 2021 to 2020.

### Buttons description
- Flash button on DIO15 used for bootloader activation (for firmware update)
- Reset button - you guess what it do.

### Notes

Coordinator backup from 2538/2652/1352 can be loaded back into another 2538/2652/1352, but into CLEAN (never used with zigbee2mqtt) chip only.
You can clear chip with zigbee2mqtt script **scripts\zStackEraseAllNvMem.js** (look about it on [Flashing page](https://github.com/egony/cc2652p_E72-2G4M20S1E/wiki/Flashing))

### Sources

As I know, sharing source codes prohibited by TI, so there is no sources here. And I can't made patches because they will include code. But you now what to do ;)

---

## Changelog (except KoenKK's patches update)

### 2021-09-02

- SDK 5.20.00.52

### 2021-08-12

- SDK 5.10.00.48

#### 2021-03-20

- LEDs now shows some events - reboot, network startup, join, data recieved
- LEDs now can be turned OFF by zigbee2mqtt config (require modifyed file zStackAdapter.js)

### 2021-02-11

- Initial release.
- SDK 4.40.04.04
- LEDs are supported
