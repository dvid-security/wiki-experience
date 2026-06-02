---
title: Flasher le STM32
description: 
published: true
date: 2026-06-02T08:09:12.832Z
tags: 
editor: markdown
dateCreated: 2026-06-02T08:09:12.832Z
---

# Configuration

Vous devez installer l'outil `stm32flash` :

```bash
apt install stm32flash
stm32flash -h
```

# Exécution

Pour flasher le firmware, suivez les étapes suivantes :

- Connectez l'UART de la carte à votre ordinateur via le dongle UART.

![uartdongleconnectedstm32.jpg](/files/flash-stm32/uartdongleconnectedstm32.jpg)

- Mettez la carte sous tension (connectez le dongle UART à votre ordinateur)

- Appuyez sur le bouton `BTLD CORE` et maintenez-le enfoncé.

![stm32_btld-core.png](/files/flash-stm32/stm32_btld-core.png)

- Appuyez sur le bouton `RESET`, puis relâchez-le.

![stm32_reset.png](/files/flash-stm32/stm32_reset.png)

- Relâchez le bouton `BTLD CORE`.

- Exécutez la commande de flashage :

```bash
stm32flash -b 115200 -w ./firmware.stm32 /dev/ttyUSB0
```

Trace d'exécution :

```bash
stm32flash Arduino_STM32_0.9

http://github.com/rogerclarkmelbourne/arduino_stm32

Using Parser : Intel HEX
Interface serial_posix: 115200 8E1
Version      : 0x22
Option 1     : 0x00
Option 2     : 0x00
Device ID    : 0x0410 (Medium-density)
- RAM        : 20KiB  (512b reserved by bootloader)
- Flash      : 128KiB (sector size: 4x1024)
- Option RAM : 16b
- System RAM : 2KiB
Write to memory
Erasing memory
Wrote address 0x080071b0 (100.00%)
```

Vous pouvez maintenant appuyer sur le bouton de réinitialisation pour redémarrer l’entraînement. Un message devrait s’afficher à l’écran.