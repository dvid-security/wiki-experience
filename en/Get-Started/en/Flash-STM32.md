---
title: Flash the STM32
description: 
published: true
date: 2026-06-02T09:01:57.243Z
tags: get started
editor: markdown
dateCreated: 2026-05-28T08:29:45.149Z
---

# **Setup**

You need to install the tool `stm32flash`:

```bash
apt install stm32flash
```

# **Run**

In order to flash the firmware, you need to process following steps:

- Connect the "UART" header of the board to your computer via a USB-UART bridge

![uartdongleconnectedstm32.jpg](/files/flash-stm32/uartdongleconnectedstm32.jpg)

- Power up the board (connect the UART dongle to your computer)
- Press and hold the "BTLD CORE" button

![stm32_btld-core.png](/files/flash-stm32/stm32_btld-core.png)

- Press, then release the "RESET" button

![stm32_reset.png](/files/flash-stm32/stm32_reset.png)

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