
# CuteCom Usage Documentation

## Introduction
CuteCom is a simple graphical interface for communicating over a serial port (UART). It is useful for testing firmware, interacting with electronic boards, or debugging serial communication.

## Installation
### On Linux (Debian/Ubuntu)
```bash
sudo apt update
sudo apt install cutecom
```

### On Fedora
```bash
sudo dnf install cutecom
```

### On Arch Linux
```bash
sudo pacman -S cutecom
```

## Launching the Application
```bash
cutecom
```
Or via the menu: Applications > Development > CuteCom.

## Serial Port Configuration
Once CuteCom is open:

* Select the serial port under **Device** (e.g., `/dev/ttyUSB0`, `/dev/ttyACM0`).
* Choose the speed (baudrate), such as **9600**, **115200**, etc.
* Set parameters : **Data bits**: usually 8 / **Parity**: None / **Stop bits**: 1 / **Flow control**: None
* Click **Open Device**.

## Sending Commands
Two methods are available:

* Type a command in the text field at the bottom and click **Send**.
* Enable **Hex output** / **Hex input** to send hexadecimal values.

## Receiving Data
Data received from the device appears in the main window.

Useful options:

* **Timestamp**: adds a timestamp to each line.
* **Log to file**: records all input/output to a log file.

## Troubleshooting
### Permission denied when opening the port
Add your user to the `dialout` group:

```bash
sudo usermod -aG dialout $USER
```
Log out and back in.

### No serial port detected
Check:

- USB cable
- USB‑serial converter (CH340, CP2102, FTDI)
- Access rights (`ls -l /dev/ttyUSB*`)

## Best Practices
- Always verify the exact serial configuration of the device.
- Close CuteCom before flashing firmware or using another serial tool.
- Enable logging for critical testing sessions.

## Conclusion
CuteCom is a fast, simple, and effective tool for working with UART interfaces without using a terminal.
