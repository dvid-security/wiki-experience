# UART

UART (**Universal Asynchronous Receiver-Transmitter**) is a hardware communication protocol used for **asynchronous** serial communication between electronic devices. Unlike SPI and I2C, which are synchronous protocols, UART does not require a clock signal. Instead, it uses a predefined baud rate to synchronize data transmission.

UART is commonly used in embedded systems, microcontrollers, and communication modules such as GPS, Bluetooth, and Wi-Fi modules.

## How UART works

UART enables two-way communication between two devices over two wires:

- TX (Transmit): Sends data.
- RX (Receive): Receives data.

Each device's TX line is connected to the RX line of the other device.

Unlike synchronous protocols, UART does not use a clock signal. Instead, both devices agree on a common baud rate (data transmission speed). Data is transmitted one bit at a time in a structured format.

Each UART transmission consists of a frame that includes:

- Start Bit (1 bit): A 0 (low voltage) is sent to indicate the beginning of data transmission.
- Data Bits (5–9 bits, typically 8 bits): The actual data being transmitted.
- Parity Bit (1 bit, optional): Used for error detection (even or odd parity).
- Stop Bit (1–2 bits): A 1 (high voltage) to signal the end of the transmission.

The baud rate defines the transmission speed in bits per second (bps). Common baud rates include:

- 9600 bps (default for many devices)
- 115200 bps (commonly used for fast communication)
- 57600, 38400, 19200, 4800 bps, etc.

**Both devices must use the same baud rate to communicate properly.**

## Features of UART

Here are some interesting and advanced features of UART:

- **DMA (Direct Memory Access)**: Reduces CPU load by handling large data transmissions automatically.
- **Hardware Flow Control (RTS/CTS)**: Additional Request to Send (RTS) and Clear to Send (CTS) signals prevent buffer overflows.
- **Half-Duplex Mode**: Uses a single wire for bidirectional communication (one direction at a time).
- **Software Serial (Bit-Banging)**: Allows UART emulation on microcontrollers without dedicated UART hardware.

## UART in everyday use

- **Embedded Systems**: Communication between microcontrollers (e.g., Arduino, Raspberry Pi, ESP32).
- **GPS Modules**: Transmitting location data over UART.
- **Bluetooth Modules (HC-05, HC-06)**: Serial communication with wireless devices.
- **Debugging & Serial Monitoring**: Used for debugging with tools like the Serial Monitor in Arduino.
- **Industrial Applications**: Communicating with sensors, motor controllers, and other peripherals.