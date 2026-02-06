# Aircrack-ng

Aircrack-ng is a network software suite for auditing wireless networks. It includes tools for detecting networks, sniffing packets, cracking WEP and WPA/WPA2-PSK keys, and analyzing 802.11 wireless LANs.

The suite works with wireless network cards that support monitor mode and can analyze 802.11a/b/g traffic.

## Main components

The Aircrack-ng suite includes several specialized tools, each designed for specific wireless network assessment tasks:

1. **aircrack-ng**: The core tool for cracking WEP and WPA/WPA2-PSK keys using various methods including FMS, PTW, KoreK, and dictionary attacks.

2. **airmon-ng**: Enables and disables monitor mode on wireless interfaces, which is necessary for capturing raw 802.11 frames.

3. **airodump-ng**: Captures raw 802.11 frames for analysis and key cracking.

4. **aireplay-ng**: Injects and replays wireless frames to generate traffic for later analysis. Can perform deauthentication attacks to force clients to disconnect and capture handshakes.

5. **airbase-ng**: Multi-purpose tool aimed at attacking clients rather than access points. Implements techniques like the Caffe Latte and Hirte attacks.

6. **airdecap-ng**: Decrypts WEP/WPA/WPA2 capture files once keys are known.

7. **airtun-ng**: Creates virtual tunnel interfaces.

8. **packetforge-ng**: Creates various types of encrypted packets that can be used for injection.

## Additional tools

The suite also includes several other specialized utilities:

- **airdecloak-ng**: Removes WEP Cloaking™ from packet capture files.
- **airdrop-ng**: Rule-based wireless deauthentication tool.
- **airgraph-ng**: Graphs wireless networks to visualize relationships.
- **airolib-ng**: Precomputes WPA/WPA2 passphrases in a database for later use with aircrack-ng.
- **airserv-ng**: Wireless card TCP/IP server allowing multiple applications to use a wireless card.

## Command line examples

Here are the most commonly used commands for the main tools in the Aircrack-ng suite:

### airmon-ng

```bash
# Check for interfering processes
airmon-ng check

# Kill interfering processes
airmon-ng check kill

# Enable monitor mode on wireless interface
airmon-ng start wlan0

# Enable monitor mode on a specific channel
airmon-ng start wlan0 6

# Disable monitor mode
airmon-ng stop wlan0mon
```

### airodump-ng

```bash
# Capture all wireless traffic in range
airodump-ng wlan0mon

# Capture traffic from a specific access point
airodump-ng --bssid 00:11:22:33:44:55 -c 6 wlan0mon

# Save captured packets to a file
airodump-ng --bssid 00:11:22:33:44:55 -c 6 -w capture wlan0mon

# Capture only WPA handshakes
airodump-ng --bssid 00:11:22:33:44:55 -c 6 -w capture --output-format pcap wlan0mon
```

### aireplay-ng

```bash
# Test injection capabilities
aireplay-ng -9 wlan0mon

# Deauthenticate all clients from an access point
aireplay-ng --deauth 0 -a 00:11:22:33:44:55 wlan0mon

# Deauthenticate a specific client
aireplay-ng --deauth 10 -a 00:11:22:33:44:55 -c AA:BB:CC:DD:EE:FF wlan0mon

# Fake authentication with an access point
aireplay-ng -1 0 -e "NetworkName" -a 00:11:22:33:44:55 -h 11:22:33:44:55:66 wlan0mon

# ARP request replay attack (for WEP cracking)
aireplay-ng -3 -b 00:11:22:33:44:55 -h 11:22:33:44:55:66 wlan0mon
```

### aircrack-ng

```bash
# Crack WEP encryption
aircrack-ng -b 00:11:22:33:44:55 capture*.cap

# Crack WPA/WPA2 using a wordlist
aircrack-ng -w wordlist.txt -b 00:11:22:33:44:55 capture*.cap

# Crack with multiple CPU cores
aircrack-ng -w wordlist.txt -b 00:11:22:33:44:55 capture*.cap -S

# Show only the password if found
aircrack-ng -w wordlist.txt -b 00:11:22:33:44:55 capture*.cap -l found_password.txt
```

### airdecap-ng

```bash
# Decrypt WEP encrypted packets
airdecap-ng -w 1A2B3C4D5E capture.cap

# Decrypt WPA/WPA2 encrypted packets
airdecap-ng -e "NetworkName" -p "password" capture.cap

# Keep only decrypted packets
airdecap-ng -w 1A2B3C4D5E -l capture.cap
```

### airolib-ng

```bash
# Create a new database
airolib-ng my_db --init

# Import a wordlist into the database
airolib-ng my_db --import passwd /path/to/wordlist.txt

# Add an ESSID to the database
airolib-ng my_db --import essid /path/to/essid.txt

# Calculate PMKs (pre-computed keys)
airolib-ng my_db --batch

# Verify the database integrity
airolib-ng my_db --verify all
```
