---
title: Flash the STM32
description: 
published: true
date: 2026-05-13T13:03:51.124Z
tags: get started
editor: markdown
dateCreated: 2026-05-13T13:03:50.324Z
---

# **Setup**

You need to install the tool `stm32flash`:

```bash
apt install stm32flash
```

# **Run**

In order to flash the firmware, you need to process following steps:

- Connect the "UART" header of the board to your computer via a USB-UART bridge

![UART Dongle Connected STM32](https://dvid-security.github.io/wiki-experience/get-started/img/uartDongleConnectedStm32.jpg)

- Power up the board (connect the UART dongle to your computer)
- Press and hold the "BTLD CORE" button

![STM32 BTLD Core](https://dvid-security.github.io/wiki-experience/get-started/img/stm32_BTLD-CORE.png)

- Press, then release the "RESET" button

![STM32 Reset](https://dvid-security.github.io/wiki-experience/get-started/img/stm32_RESET.png)

- Release the "BTLD CORE" button
- Execute the flash command

```bash
stm32flash -b 115200 -w ./firmware.stm32 /dev/ttyUSB0
```

Execution trace :

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

You can now press the reset button to restart the training, something should appear on the screen.