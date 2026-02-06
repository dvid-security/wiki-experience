# Wi-Fi

Wi-Fi is a family of wireless network protocols based on the IEEE 802.11 standards, commonly used for local area networking of devices. It is a trademark of the Wi-Fi Alliance, which restricts the use of the term "Wi-Fi Certified" to products that successfully complete interoperability certification testing.

Since 2019, more than 3.05 billion Wi-Fi-enabled devices are shipped globally each year.

## Wi-Fi Versions

Wi-Fi has evolved through several IEEE standardized versions:

- **Original (1997)**: First specification with FHSS (1 Mbps) and DSSS (1-2 Mbps) methods in the 2.4 GHz band.
- **802.11b (1999) - Wi-Fi 1**: First major standard, speeds up to 11 Mbps in the 2.4 GHz band.
- **802.11a (1999) - Wi-Fi 2**: Used OFDM, speeds up to 54 Mbps in the 5 GHz band.
- **802.11g (2003) - Wi-Fi 3**: Increased speed to 54 Mbps in the 2.4 GHz band using OFDM.
- **802.11n (2009) - Wi-Fi 4**: Used multiple antennas for speeds up to 450 Mbps, compatible with both 2.4 GHz and 5 GHz bands.
- **802.11ac (2012) - Wi-Fi 5**: Operates in the 5 GHz band with gigabit speeds.
- **802.11ax (2021) - Wi-Fi 6**: Works in both 2.4 GHz and 5 GHz bands with multi-gigabit speeds. Wi-Fi 6E adds the 6 GHz band.
- **802.11be (2023) - Wi-Fi 7**: Operates in the same three bands as Wi-Fi 6E, with expected speeds up to 40 Gbps.

## How Wi-Fi Works

Wi-Fi works by sending data packets via radio waves over different channels. Devices communicate by modulating and demodulating carrier waves.

### Key Components

- **Wi-Fi Stations**: All devices equipped with Wi-Fi capabilities.
- **Access Points**: Devices that allow stations to connect to a wired network.
- **Channels**: Subdivisions of radio bands used for transmission.
- **MAC Addresses**: Unique 48-bit identifiers programmed into each station.

### Communication Stack

Wi-Fi is part of the IEEE 802 family of protocols. Data is organized into 802.11 frames at the data link layer, similar to Ethernet frames but with additional address fields needed for wireless communication.

The MAC and physical layer specifications are the technical rules that determine how Wi-Fi devices transmit and receive radio signals across the 2.4, 5, and 6 GHz frequency bands.

### Transmission Mechanism

Wi-Fi uses CSMA/CA (Carrier-Sense Multiple Access with Collision Avoidance) to manage how devices share the wireless medium. Before transmitting, devices check if the channel is clear to avoid collisions.

Channels operate in half-duplex mode, meaning devices can either transmit or receive at one time, but not both simultaneously. Multiple networks can share the same channel, though this may reduce performance.

## Wi-Fi Channels

Wi-Fi channels are specific frequency ranges within each band that devices use to communicate.

### Channel Basics

Think of Wi-Fi channels like lanes on a highway - they allow multiple devices to communicate without interfering with each other. Each Wi-Fi band contains multiple channels:

- **2.4 GHz band**: Contains 11-14 channels (depending on country)
- **5 GHz band**: Contains 24+ non-overlapping channels
- **6 GHz band**: Contains up to 59 channels (newest addition)

### Channel Numbering and Characteristics

#### 2.4 GHz Band
- Numbered from 1 to 14 (most countries use 1-11 or 1-13)
- Only channels 1, 6, and 11 don't overlap with each other
- Provides better range but more interference from other devices

#### 5 GHz Band
- Numbered non-consecutively (36, 40, 44, 48, etc.)
- All channels are non-overlapping
- Better speeds but shorter range than 2.4 GHz

#### 6 GHz Band
- Newest band with many available channels
- Highest speeds but shortest range
- Less congestion than other bands

### Channel Width

Channel width determines how much of the frequency spectrum a connection uses:

- **20 MHz**: Standard width
- **40 MHz**: Twice as wide, potentially twice as fast
- **80 MHz**: Four times as wide
- **160 MHz**: Eight times as wide

Wider channels provide faster speeds but are more susceptible to interference.

## Key Wi-Fi Terminology

Understanding the following terms is essential for effective network management and troubleshooting:

### BSSID (Basic Service Set Identifier)

The BSSID is the MAC physical address of the access point or wireless router used to connect to the Wi-Fi network. It's a unique 48-bit identifier that distinguishes between multiple access points within a wireless network.

Key points about BSSID:
- It's based on the MAC address of the access point's wireless adapter
- Each access point in a network has its own unique BSSID
- Users typically don't notice when their device switches from one BSSID to another

### SSID (Service Set Identifier)

The SSID is the name of a wireless network that users see when searching for available Wi-Fi connections. It's a human-readable identifier that allows users to distinguish between different networks.

Key points about SSID:
- Can be up to 32 octets (characters) long
- Typically displayed in natural language (like "HomeWiFi" or "OfficeNetwork")
- Broadcast by access points to announce the presence of a network
- Multiple access points can share the same SSID in larger networks

### ESSID (Extended Service Set Identifier)

The ESSID is essentially the SSID used in a network with multiple access points. It represents the entire Wi-Fi network rather than an individual access point.

Key points about ESSID:
- Often used interchangeably with SSID
- Helps create a unified network experience across different physical locations

## Range and Performance

Wi-Fi radio bands work best in line-of-sight conditions. Common obstacles like walls can significantly reduce range, but this also helps minimize interference between different networks in crowded environments.

The range of an access point is about 20 meters (66 feet) indoors, while some access points claim a range of up to 150 meters (490 feet) outdoors.

Over time, the speed and spectral efficiency of Wi-Fi have increased. As of 2019, some versions of Wi-Fi, operating on suitable hardware at short range, can achieve speeds of 9.6 Gbit/s.

### Channel Selection Tips

- For 2.4 GHz networks, stick to channels 1, 6, or 11 to avoid overlap
- Use channel scanning tools to identify the least congested channels in your area
- Consider using the 5 GHz band in dense environments for less interference
- Modern routers can automatically select channels, but manual selection may be better in high-density environments

## Security Considerations

Securing Wi-Fi networks is essential to protect your data. Here are the main measures to take:

- **Change Default Passwords**: First line of defense to protect your network, change both the default administrator password and the default SSID name to something unique.
- **Implement Strong Encryption**: Use WPA3 protocol (currently the strongest) to encrypt information transmitted between routers and wireless devices.
- **Segment Your Network**: Separate sensitive devices or data from the rest of your network for additional protection, especially for IoT devices.
- **Set Up a Guest Network**: Create a separate network for visitors to keep them isolated from your main network and sensitive devices.
- **Keep Router Firmware Updated**: Regularly update your router's software to patch security vulnerabilities.