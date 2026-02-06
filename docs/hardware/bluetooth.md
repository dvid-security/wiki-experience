# Bluetooth

Bluetooth is a short-range wireless communication protocol designed for exchanging data between devices over a short distance using radio waves. It operates in the 2.4 GHz ISM (Industrial, Scientific, and Medical) band and is widely used for connecting devices such as smartphones, laptops, headphones, wearables, and IoT devices.

Originally developed in 1994 by Ericsson, Bluetooth has evolved into a versatile protocol for both data transfer and low-power wireless communication.

## Bluetooth versions

Bluetooth has undergone several updates to improve its functionality and security:

- 1.0 and 1.1 (1999): Initial release with basic functionality.
- 2.0 + EDR (2004): Introduced Enhanced Data Rate (3 Mbps).
- 3.0 + HS (2009):	Added support for faster transfer (up to 24 Mbps) using Wi-Fi.
- 4.0 (2010): Introduced Bluetooth Low Energy (BLE).
- 4.2 (2014): Improved security and support for IPv6.
- 5.0 (2016): Increased range (up to 240m), speed (2 Mbps), and broadcasting capacity.
- 5.1 (2019): Introduced direction finding for location-based services.
- 5.2 (2020): Enhanced audio with LE Audio and support for Isochronous Channels.
- 5.3 (2021): Improved energy efficiency and performance.

## How Bluetooth works

Bluetooth operates on the principle of device pairing and communication over short distances, typically up to 10 meters (33 feet) for standard Bluetooth and up to 100 meters (328 feet) for Bluetooth Class 1 devices.

### Key components

Bluetooth presents with 3 key components:

- Devices:
	- Central Device (Master): Initiates and manages communication (e.g., a smartphone).
	- Peripheral Device (Slave): Responds to the central device (e.g., a wireless speaker or fitness tracker).
- Piconet: A small network of devices connected via Bluetooth. One central device can connect to up to 7 active peripherals.
- Frequency Hopping: Bluetooth divides the 2.4 GHz band into 79 channels and uses frequency hopping spread spectrum (FHSS) to switch between channels up to 1600 times per second. This reduces interference and improves reliability.

Bluetooth uses standardized profiles to define how devices communicate for specific use cases. Here are some popular profiles include:

- **HFP** (Hands-Free Profile): Used for hands-free calling (e.g., in car systems).
- **A2DP** (Advanced Audio Distribution Profile): Transmits high-quality audio.
- **HID** (Human Interface Device Profile): For keyboards, mice, and game controllers.
- **SPP** (Serial Port Profile): Emulates serial communication over Bluetooth.
- **GATT** (Generic Attribute Profile): Used by Bluetooth Low Energy (BLE) devices.

### Workflow

The Bluetooth workflow is divided in two steps: the discovery and pairing, and the communication phase.

#### Device discovery and pairing

Here are the first phases of device discovery and pairing:

1. Discovery: Devices scan for others within range. A device may be in discoverable mode to advertise its presence.
2. Pairing: Establishes a secure link between devices using methods such as:
	- PIN codes.
	- Numeric Comparison (user verifies matching codes).
	- Just Works (no authentication for low-security use cases).
3. Bonding: After pairing, devices store a long-term key to reconnect without re-pairing.

#### Communication phase

After the pairing phase, the devices can start to communicate:

1. Connection Establishment: The central device initiates a connection to a peripheral.
2. Data Exchange: Devices communicate using profiles and protocols (e.g., audio streaming or file transfer).
3. Disconnection: Devices can terminate the connection when the communication is complete.

## Security considerations with Bluetooth

Since Bluetooth is commonly used in IoT, security is a major concern. Standard security practices include:

- **Encryption**: Uses AES encryption to protect data during transmission.
- **Authentication**: Pairing methods prevent unauthorized devices from connecting.
- **Secure Simple Pairing (SSP)**: Modern Bluetooth versions use SSP for stronger security during pairing.
- **Passive Eavesdropping Protection**: Frequency hopping minimizes the risk of interception.

## Bluetooth in everyday use

As aleady said, the Bluetooth protocol is widely used. Here are some examples of usage:

- **Audio Devices**: Wireless headphones, speakers, and hearing aids use profiles like A2DP and HFP.
- **IoT Devices**: Smart home devices (e.g., locks, thermostats, and lights).
- **Wearables**: Fitness trackers and smartwatches for health monitoring and notifications.
- **Proximity Beacons**: Location-based services like indoor navigation or retail promotions.
- **File Transfer**: Sending files between phones, tablets, or computers.
- **Game Controllers**: Bluetooth HID profile for connecting keyboards, mice, and controllers.