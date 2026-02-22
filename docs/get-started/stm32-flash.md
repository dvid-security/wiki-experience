# Flash the STM32 side of my DVID

## Setup
You need to install the tool `stm32flash`:

```bash
git clone https://github.com/dvid-security/Arduino_STM32
./Arduino_STM32/tools/linux64/stm32flash/stm32flash -h
```

# Run

In order to flash the firmware, you need to process following steps:

1. Connect the "UART" header of the board to your computer via a USB-UART bridge

![UART Dongle Connected STM32](../img/uartDongleConnectedStm32.jpg)

2. Power up the board (connect the UART dongle to your computer)

3. Press and hold the "BTLD CORE" button

![STM32 BTLD Core](../img/stm32_BTLD-CORE.png)

4. Press, then release the "RESET" button

![STM32 Reset](../img/stm32_RESET.png)

5. Release the "BTLD CORE" button

6. Execute the flash command

```bash
#> ./Arduino_STM32/tools/linux64/stm32flash/stm32flash -b 115200 -w ./firmware.stm32 /dev/ttyUSB0
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
