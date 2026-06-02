---
title: Flasher l'ESP32
description: 
published: true
date: 2026-06-02T07:52:49.451Z
tags: 
editor: markdown
dateCreated: 2026-06-02T07:52:49.450Z
---

# Configuration

Vous devez installer l'outil `esptool` :

```bash
pip install esptool
esptool -h
```

# Mappage

Concernant le firmware, les éléments suivants sont disponibles :

- `0x1000` : chargeur de démarrage
- `0x8000` : partitions
- `0x10000` : firmware

# Exécution

Pour flasher le firmware, suivez les étapes suivantes :

- Connectez l'UART de la carte à votre ordinateur via l'adaptateur USB-UART.

![uartdongleconnectedesp32.png](/files/flash-esp32/uartdongleconnectedesp32.png)

- Mettez la carte sous tension (connectez le dongle UART à votre ordinateur).

- Appuyez sur le bouton « BTLD CORE » et maintenez-le enfoncé.

![esp32_btld-core.png](/files/flash-esp32/esp32_btld-core.png)

- Appuyez sur le bouton « RESET », puis relâchez-le.

![esp32_reset.png](/files/flash-esp32/esp32_reset.png)

- Relâchez le bouton « BTLD CORE ».

- Exécutez la commande de flashage :

```bash
esptool --port /dev/ttyUSB0 --baud 115200 --chip esp32 write-flash 0x10000 ./firmware.esp32
```

Trace d'exécution :

```bash
esptool.py v4.6.2
Serial port /dev/ttyUSB0
Connecting........
Chip is ESP32-D0WD-V3 (revision v3.1)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: 94:54:c5:d8:23:58
Uploading stub...
Running stub...
Stub running...
Configuring flash size...
Flash will be erased from 0x00000000 to 0x003fffff...
Compressed 4194304 bytes to 191559...
Wrote 4194304 bytes (191559 compressed) at 0x00000000 in 29.8 seconds (effective 1124.6 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...
```

Vous pouvez maintenant appuyer sur le bouton de réinitialisation pour redémarrer l'entraînement. Un message devrait s'afficher à l'écran.

# Recrutement

- Chargeur de démarrage : [esp32_bootloader.bin](/files/flash-esp32/esp32_bootloader.bin)

- Partition : [esp32_partitions.bin](/files/flash-esp32/esp32_partitions.bin)

```bash
esptool --port /dev/ttyUSB0 --baud 115200 --chip esp32 write-flash 0x1000 bootloader.bin 0x8000 esp32_partitions.bin 0x10000 ./[FIRMWARE]
```