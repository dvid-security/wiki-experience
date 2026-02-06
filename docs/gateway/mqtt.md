# MQTT

MQTT (**Message Queuing Telemetry Transport**) is a lightweight, publish-subscribe messaging protocol designed for constrained devices and low-bandwidth, high-latency, or unreliable networks. It is widely used in Internet of Things (IoT) applications for efficient communication between sensors, devices, and servers.

Originally developed in 1999 by IBM, MQTT has become a popular protocol for IoT due to its simplicity, low resource requirements, and support for real-time messaging.

## MQTT versions

MQTT has undergone several updates to improve its functionality and security:

- MQTT 3.1 (2010): The first widely adopted version, introducing key features like QoS.
- MQTT 3.1.1 (2014): Enhanced interoperability and clarified specifications.
- MQTT 5.0 (2019): Introduced major improvements, such as:
	- User-defined properties for custom metadata.
	- Negative acknowledgments (NACK) for rejected messages.
	- Enhanced error reporting and scalability.

## How MQTT works

MQTT operates on a publish-subscribe model, differing from the traditional client-server model of protocols like HTTP. Instead of a direct connection between devices, MQTT relies on a central broker to manage communication.

### Key components

MQTT works with 3 key components:

- Broker: The central server that routes messages between devices. Examples of brokers include Eclipse Mosquitto, HiveMQ, and AWS IoT Core.
- Clients: Devices or applications that connect to the broker. Clients can:
	- Publish messages to topics.
	- Subscribe to topics to receive messages.
- Topics: Messages are categorized into topics (e.g., home/temperature) to organize communication. Clients subscribe to these topics to receive relevant data and can publish to topics.

Typically, MQTT runs over TCP but it also supports WebSocket. The default ports are 1883 (**unencrypted**) and 8883 (TLS **encrypted**).

Similarly to HTTP, a **Keep-Alive** mechanism ensures clients remain connected to the broker.

### Workflow

The MQTT workflow is divided into 3 phases:

1. A client publishes a message to a topic (e.g., home/livingroom/temperature).
2. The broker receives the message and forwards it to all clients that have subscribed to that topic.
3. Subscribed clients receive the message in real time.

Here is a simple example of a MQTT workflow:

1. A temperature sensor publishes data to the topic home/livingroom/temperature, and a mobile app subscribes to the same topic to display temperature updates.
2. The sensor sends a message: `{"temperature": 22.5}` to the broker. The broker forwards the message to all subscribers of the topic and the mobile app receives the message and updates the user interface.
3. The mobile app can publish commands (e.g., `turn_off`) to a topic like home/livingroom/thermostat/command, which the thermostat device subscribes to.

## Features of MQTT

Here are the main features and "charcteristics" of MQTT:

- **Lightweight and Efficient**: Designed for devices with limited processing power and memory, MQTT uses minimal bandwidth.
- **Publish-Subscribe Model**: Decouples message senders (publishers) from receivers (subscribers), improving scalability.
- **Quality of Service (QoS)**: MQTT ensures reliable message delivery with three QoS levels:
	- QoS 0: "At most once" delivery. Messages are sent without confirmation.
	- QoS 1: "At least once" delivery. Messages are sent until acknowledged by the receiver.
	- QoS 2: "Exactly once" delivery. Ensures the message is received only once, even if duplicates occur.
- **Retained Messages**: A published message can be retained by the broker, allowing new subscribers to receive the most recent message immediately.
- **Will Messages**: Allows clients to define a "last will" message that the broker sends if the client disconnects unexpectedly.
- **Persistent Sessions**: Supports persistent client sessions, enabling reconnection without losing subscription or message state.
- **Security**: While MQTT itself does not enforce security, encryption (via TLS) and authentication (via username/password or certificates) are commonly used.

## Security considerations with MQTT

Since MQTT is commonly used in IoT, security is a major concern. Standard security practices include:

- **Encryption**: Use TLS/SSL to encrypt messages, ensuring confidentiality.
- **Authentication**: Username/password for basic authentication and certificates for mutual TLS authentication.
- **Access Control**: Brokers can enforce topic-level permissions, ensuring clients can only publish/subscribe to authorized topics.
- **Firewalls**: Restrict MQTT communication to trusted IP ranges and ports.

## MQTT in everyday use

MQTT is ideal for scenarios where efficiency and reliability are critical, particularly in IoT environments:

- **IoT and Smart Home Devices**:
	- Communicating sensor data (e.g., temperature, humidity).
	- Controlling devices (e.g., turning on lights or adjusting thermostats).

- **Industrial IoT (IIoT)**:
	- Monitoring equipment health and performance.
	- Sending real-time alerts for machinery.

- **Connected Vehicles**:
	- Exchanging data between vehicles and servers (e.g., GPS, speed).
	- Fleet management systems.

- **Healthcare**:
	- Wearable devices transmitting patient data (e.g., heart rate, blood pressure).
	- Remote monitoring of medical equipment.

- **Energy and Utilities**:
	- Smart grids for monitoring energy consumption.
	- Communication between solar panels and central systems.