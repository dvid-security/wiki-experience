
# I²C Protocol

The **I²C** (Inter‑Integrated Circuit) protocol is a synchronous serial communication bus widely used in embedded systems to connect microcontrollers with peripheral devices such as sensors, memory chips, audio controllers, displays, and more.
Originally developed by **Philips** in **1982**, it has since become a standard maintained by **NXP** and adopted across the electronics industry.

---

# 1. Bus Architecture

## Two‑Wire Communication
The I²C bus uses only two main signal lines:
- **SDA** — Serial Data Line (bidirectional)
- **SCL** — Serial Clock Line (bidirectional)

A common ground reference is required for all devices.

Both lines operate in **open‑drain** (or open‑collector) mode, meaning devices can only pull lines *low*. Pull‑up resistors keep the lines *high* when released. This mechanism prevents electrical contention and allows multiple devices—including multiple masters—to share the bus safely.

## Topology and Addressing
I²C supports:
- **One or more masters**
- **One or multiple slaves**

The master always initiates communication and generates the clock signal.
Devices are usually addressed using **7‑bit addresses** (up to 128 possible nodes, with some reserved). A **10‑bit addressing mode** also exists.

---

# 2. Start and Stop Conditions

Every I²C transaction begins and ends with specific line transitions:

- **START condition**:
  SDA transitions from `1 → 0` while SCL remains at `1`
- **STOP condition**:
  SDA transitions from `0 → 1` while SCL is `1`

These markers let devices detect when the bus becomes busy or free.

---

# 3. Data Transmission

## Byte‑Based Communication
Data transfers occur **one byte at a time**.
Each byte must be followed by a bit of acknowledgment:

- **ACK (0)** — receiver confirms successful reception
- **NACK (1)** — indicates the end of communication or a missing device

## Address + Read/Write Bit
An I²C transfer starts with sending:
- **7‑bit slave address**
- **1 bit indicating direction**:
  - `0` → Write
  - `1` → Read

## Supported Speeds
I²C supports several standardized data rates:
- **Standard Mode**: 100 kbit/s
- **Fast Mode**: 400 kbit/s
- **Fast Mode+**: 1 Mbit/s
- **High‑Speed Mode**: 3.4 Mbit/s
- **Ultra‑Fast Mode**: unidirectional, limited to specific applications

---

# 4. Electrical Behavior: Open‑Drain and Pull‑Ups

With open‑drain outputs, devices can only pull the line low. The idle state (`1`) is maintained by **pull‑up resistors**, typically between **4.7 kΩ and 10 kΩ**.
This setup:

- avoids short‑circuits between devices
- enables multi‑master arbitration (low level is dominant)
- allows a shared line design suitable for many components

---

# 5. Typical I²C Communication Sequence

A standard transaction follows these steps:

1. Master checks that the bus is idle (SDA = 1, SCL = 1).
2. Master issues a **START** condition.
3. Master sends the **address byte + R/W bit**.
4. Slave responds with **ACK**.
5. Master and slave exchange one or more bytes.
6. Each byte is followed by ACK/NACK.
7. Master sends a **STOP** condition to release the bus.

---

# 6. Applications of I²C

I²C is extremely common in embedded and consumer electronics thanks to its flexibility and minimal wiring.
It is used in:

- On DVID, the SSD1306 (screen) is controlled over I2C
- Sensor interfaces (temperature, pressure, IMU)
- EEPROMs and serial memory chips
- RTC (Real‑Time Clock) modules
- Audio processors and codecs
- LCD / LED display drivers
- GPIO expanders
