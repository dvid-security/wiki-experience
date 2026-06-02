---
title: Flasher l'ESP32-C6
description: 
published: true
date: 2026-06-02T09:13:10.061Z
tags: 
editor: markdown
dateCreated: 2026-06-02T07:59:03.991Z
---

# Configuration

Vous devez installer l'outil `esptool.py` :

```bash
pip install esptool
esptool -h
```

Vous devez télécharger les fichiers suivants :

- [espc6_bootloader.bin](/files/flash-esp32c6/espc6_bootloader.bin)

- [espc6_partition-table.bin](/files/flash-esp32c6/espc6_partition-table.bin)

- [espc6_com-at.bin](/files/flash-esp32c6/espc6_com-at.bin)

Certains tutoriels nécessitent le firmware ESP-AT. Son utilisation requiert une modification du câblage interne. Cette procédure permet de flasher entièrement l'ESP32-C6. Le téléchargement du bootloader et de la carte mémoire n'est pas nécessaire.

```bash

# Télécharger le binaire brut 4.0.0.0 (fonctionne correctement)

https://docs.espressif.com/projects/esp-at/en/latest/esp32c6/AT_Binary_Lists/esp_at_binaries.html

# Télécharger l'outil de configuration du câblage :

wget https://raw.githubusercontent.com/espressif/esp-at/b1a323e9580354d584591dcbddce372e87734a85/tools/at.py

unzip ESP32-C6-4MB-AT-V4.0.0.0.zip

mv ESP32-C6-4MB-AT-V4.0.0.0/ESP32-C6-4MB-V4.0.0.0/factory/factory_ESP32C6-4MB.bin .

python at.py modify_bin --tx_pin 1 --rx_pin 0 --cts_pin -1 --rts_pin -1 --input factory_ESP32C6-4MB.bin

esptool.py -p /dev/ttyUSB0 -b 921600 --chip esp32c6 write_flash --flash_mode dio --flash_size 4MB --flash_freq 80m 0x0 target.bin

```

# Mapping

Concernant le firmware, les éléments suivants sont disponibles :

- `0x1000` : espc6_bootloader.bin
- `0x8000` : espc6_partition-table.bin
- `0x10000` : espc6_com-at.bin

# Flash

Pour flasher, maintenez le bouton `BTLD RADIO` enfoncé, puis appuyez brièvement sur `COLD RESTART`. Maintenez le bouton `BTLD RADIO` enfoncé jusqu'au démarrage du processus de flash du firmware. Une fois le processus lancé, vous pouvez relâcher le bouton.

# Câblage

Pour flasher l'ESP32-C6, vous devez câbler votre dongle UART comme indiqué sur l'image suivante :

![wiringc6.jpg](/files/flash-esp32c6/wiringc6.jpg)

# **Exécution**

```bash
esptool --port /dev/ttyUSB0 --baud 115200 --chip esp32c6 write-flash 0x1000 espc6_bootloader.bin 0x8000 espc6_partition-table.bin 0x10000 espc6_com-at.bin
```

Console :

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