# Flash the ESP32-C6 MCU of my DVID

## Setup
You need to install the tool `esptool.py`:

```bash
pip install esptool
esptool.py -h
```

## Mapping
Regarding the firmware, following parts are available :

* 0x1000 : bootloader
* 0x8000 : partitions
* 0x10000 : firmware

# Run

```bash
esptool.py --port /dev/ttyUSB0 --baud 115200 --chip esp32c6 write_flash 0x1000 bootloader.bin 0x8000 partitions.bin 0x10000 firmware.bin
```
