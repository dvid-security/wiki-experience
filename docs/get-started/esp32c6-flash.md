# Flash the ESP32-C6 MCU of my DVID

## Setup
You need to install the tool `esptool.py`:

```bash
pip install esptool
esptool.py -h
```

You need to download those files :

* [espc6_bootloader.bin](./files/espc6_bootloader.bin)

* [espc6_partition-table.bin](./files/espc6_partition-table.bin)

* [espc6_com-at.bin](./files/espc6_com-at.bin)

## Mapping

Regarding the firmware, following parts are available :

* 0x1000 : espc6_bootloader.bin

* 0x8000 : espc6_partition-table.bin

* 0x10000 : espc6_com-at.bin

## Flash

To flash, press and hold the `BTLD RADIO` button, then briefly click the `COLD RESTART` button. Keep holding the `BTLD RADIO` button until the flashing process starts.
Once the process begins, you can release the button.

## Wiring
To flash the ESPC6, you need to wire your UART dongle according the following picture :

![Wiring ESPC6](./img/wiringC6.jpg)

# Run

```bash
esptool.py --port /dev/ttyUSB0 --baud 115200 --chip esp32c6 write_flash 0x1000 espc6_bootloader.bin 0x8000 espc6_partition-table.bin 0x10000 espc6_com-at.bin
```

Console trace
```bash
esptool.py v4.10.dev2
Serial port /dev/ttyUSB0
Connecting....
Chip is ESP32-C6 (QFN40) (revision v0.0)
Features: WiFi 6, BT 5, IEEE802.15.4
Crystal is 40MHz
MAC: 40:4c:ca:ff:fe:55:44:30
MAC BASIC: 40:4c:ca:55:44:30
MAC_EXT: ff:fe
Uploading stub...
Running stub...
Stub running...
Configuring flash size...
Flash will be erased from 0x00010000 to 0x00139fff...
Compressed 1220480 bytes to 677594...
Wrote 1220480 bytes (677594 compressed) at 0x00010000 in 59.9 seconds (effective 163.0 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin..
```
