---
title: NMAP
description: 
published: true
date: 2026-06-09T09:17:08.711Z
tags: tools
editor: markdown
dateCreated: 2026-06-09T09:17:08.711Z
---

Nmap (Network Mapper) is an essential open-source tool for network exploration and security auditing. 
Practically, it allows you to map a network to discover which devices are connected to it and to identify the open entry points (the "ports") on these machines.

# Port States

During a scan, Nmap interrogates the ports of a machine (a basic command scans over 1,660 ports by default) and categorizes them into different states. 

Here are the three main states a beginner should know:

- `Open`: An application is actively listening on this port and accepting connections. This is often the primary target during an audit.

- `Closed`: The port is accessible and responds, but no application is currently using it.

- `Filtered`: Nmap cannot determine whether the port is open or closed because a firewall (or a network device) is blocking the requests.

# Basic Commands

Here are the most useful commands to get started. 
Open your terminal and replace 192.168.1.1 with the IP address of your target.

## Simple scan of a machine

This command launches a standard scan to find open ports on a specific IP address.

```bash
nmap 192.168.1.1
```

## Scan an entire network

Ideal for seeing who is connected to your local Wi-Fi network without scanning ports (replace with your network range).

```bash
nmap -sn 192.168.1.0/24
```

## Scan a specific port or a range of ports

To save time, you can target only one port (e.g., 80 for the web) or a range of ports.

```bash
nmap -p 80 192.168.1.1
nmap -p 1-100 192.168.1.1
```