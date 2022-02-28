# Zigbee Coordinator Firmware for RF-STAR RF-BM-2652P2 module (cc2652p chip)

## Firmware description

Based on [Koenkk](https://github.com/Koenkk/Z-Stack-firmware/blob/master/coordinator/Z-Stack_3.x.0/firmware.patch) and [JetHome](https://github.com/jethome-ru/zigbee-firmware/tree/master/ti/coordinator/cc2652) patches for Z-Stack_3.x.0.

### Changes from original firmware
- Default TX power: 20dBm.
- Extended LEDs support

Actually this firmware now is very similar to [JetHome firmware](https://github.com/jethome-ru/zigbee-firmware/tree/master/ti/coordinator/cc2652).

### TX power ajust

Power can be adjusted in zigbee2mqtt config:

    experimental:
      transmit_power: 5

Available TX power values: -20, -18, -15, -12, -10, -9, -6, -5, -3, 0, 1..20

### LEDs description
- Green (DIO7) turns ON when the network is running, blinking when joining enable
- Red (DIO6) flashed when APS frame received
- When stick restarted - both double blinking (depends on zigbee-heardsman status and **disable_led** configuration)

Leds can be turned OFF/ON by zigbee2mqtt config.

### Buttons description
- Flash button on DIO15 used for bootloader activation (for firmware update)
- Reset button - you guess what it do.

### Notes

Strongly recommended to clear the memory after flashing (look about it on [Flashing page](https://github.com/egony/cc2652p_E72-2G4M20S1E/wiki/Flashing)).

---

## Changelog

### 2022-03-02

- SDK 5.40.00.40

### 2022-02-18

- Built for CC1352P1F chip variant due to compiling for CC2652P1F chip variant produce same code now.
- LEDs support code copy-pasted from [JetHome patches](https://github.com/jethome-ru/zigbee-firmware/tree/master/ti/coordinator/cc2652) for code compatibility and easy maintenance. But...
- Hard reset (or unplug-plug) not required now when changing **disable_led** false -> true in configuration (restart z2m still required).

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
