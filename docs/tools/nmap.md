# Nmap

`nmap` is a powerful and versatile tool widely used in network security and administration.

`nmap` (short for Network Mapper) is an open-source tool designed for network exploration, security auditing, and vulnerability scanning. It is primarily used to discover hosts and services on a network, assess their security posture, and gather information about them.

`nmap` is widely used by network administrators, security professionals, and ethical hackers to map networks, identify vulnerabilities, and monitor open ports and running services. Its functionality can be extended with additional scripts and tools.

## Main usages

1. Network Discovery: It can identify active hosts on a network, helping to map out the devices connected to an infrastructure.
2. Port Scanning: ``nmap`` scans for open ports on devices, revealing which services (e.g., HTTP, FTP, SSH) are running and accessible.
3. Service and Version Detection: `nmap` can detect the services running on open ports and determine their software versions.
4. Operating System Detection: By analyzing network responses, `nmap` can guess the operating system of the target device.
5. Vulnerability Assessment: With its scripting engine (NSE - Nmap Scripting Engine), `nmap` can check for known vulnerabilities and misconfigurations in network services.
6. Firewall Evasion and Stealth Scanning: It provides options to bypass firewalls, IDS/IPS systems, or scan in a less detectable manner.
7. Performance and Scalability: `nmap` works well on networks of all sizes, from small LANs to large, distributed networks.

## Command line examples

This section will present some basic `nmap` usages.

### Basic ping scan

`nam` can find devices that are active on the network:

```bash
nmap -sn 192.168.1.0/24
```

This scans the subnet `192.168.1.0/24` to list all active devices (ping only).

### Scan for open ports

Check which ports are open on a specific host:

```bash
nmap 192.168.1.10
```

By default, this scans the 1,000 most common TCP ports.

### Detect service versions

Identify the services and their versions running on open ports:

```bash
nmap -sV 192.168.1.10
```

### Perform an OS detection scan

`nmap` is also able to guess the operating system running on a target:

```bash
nmap -O 192.168.1.10
```

### Scan a range of IPs

It is also possible to scan multiple hosts by specifying a range of IP addresses:

```bash
nmap 192.168.1.1-100 192.168.2.0/24
```

Multiple targets and ranges can be added into a single command.

### Scan specific ports

To scan specific ports (e.g., 22 and 80):

```bash
nmap -p 22,80 192.168.1.10
```

To perform a full scan on the 65535 TCP ports, the `-p-` parameter can be used.

### UDP scan

By default, `nmap` only scan the TCP ports. `-sU` must be indicated to scan the UDP ports:

```bash
nmap -sU 192.168.1.1
```

### Run vulnerability scans with NSE

Using Nmap's scripting engine, it can run security scripts. For example:

```bash
nmap --script vuln 192.168.1.10
```

This uses vulnerability detection scripts from the NSE.

### Stealth scan

To avoid triggering alarms on firewalls or IDS, you can use a SYN scan:

```bash
nmap -sS 192.168.1.10
```

This will only perform the SYN request of the TCP exchange, and `nmap` will not perform the full exchange. However, this method is now more detected as it was in the past.

### Save scan results

It is also possible to save the scan results to a file for later analysis:

```bash
nmap -oN scan_results.txt 192.168.1.10
```

## Useful options

This section presents some useful `nmap` options:

```
-sn	Ping scan (no port scanning).
-sS	SYN scan (stealth scan).
-sU UDP scan.
-sV	Detect service versions.
-O	Detect the operating system.
-p	Specify ports to scan.
--script	Run Nmap Scripting Engine (NSE) scripts.
-sC Run the default NSE scripts, equivalent to --script=safe,intrusive.
-oN	Save results in a human-readable format.
-oX	Save results in XML format.
-T	Adjust the speed of the scan (0-5).
```