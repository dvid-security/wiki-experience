# Nmcli

`nmcli` is a powerful command-line tool for controlling NetworkManager and reporting network status. It can be used as a replacement for graphical network management tools, especially on servers, headless machines, and terminals where no GUI is available.

## Main usages

1. **Network Connection Management**: Create, display, edit, delete, activate, and deactivate network connections.
2. **Device Control**: Monitor and control network device status.
3. **Script Automation**: Utilize NetworkManager via `nmcli` instead of managing network connections manually.
4. **Server Administration**: Control NetworkManager without a GUI, including creating, editing, starting and stopping network connections.
5. **Network Status Monitoring**: View detailed information about network connections and devices.

## Command line examples

This section presents some basic `nmcli` usages.

### Check NetworkManager status

```bash
nmcli general status
```

This displays the overall status of NetworkManager, including connectivity state and hardware status.

### View network connections

```bash
nmcli connection show
```

Lists all network connections that NetworkManager has configured.

### View only active connections

```bash
nmcli connection show --active
```

Shows only the currently active network connections.

### View network devices status

```bash
nmcli device status
```

Displays all network devices recognized by NetworkManager and their current state.

### Turn Wi-Fi on or off

```bash
nmcli radio wifi on
```

Or to turn it off:

```bash
nmcli radio wifi off
```

### Connect to a Wi-Fi network

```bash
nmcli dev wifi connect "SSID_Name" password "wifi_password" name "Connection_Name"
```

Creates a new connection profile and connects to the specified Wi-Fi network.

### Activate an existing connection

```bash
nmcli con up id "Connection_Name"
```

Or using the connection's UUID:

```bash
nmcli con up uuid 6b028a27-6dc9-4411-9886-e9ad1dd43761
```

### Disconnect a device

```bash
nmcli dev disconnect iface eth0
```

Disconnects the connection on the specified interface and marks the device as unavailable for auto-connecting.

### View available Wi-Fi networks

```bash
nmcli dev wifi
```

Lists all available Wi-Fi access points known by the NetworkManager.

### View detailed information about a specific connection

```bash
nmcli con show id "Connection_Name"
```

Displays all details of the connection with the specified name.

## Useful options

This section presents some useful `nmcli` options:

```
-t, --terse: Output in terse mode (better for script processing)
-p, --pretty: Output in pretty mode (human-readable, aligned values)
-f, --fields: Specify which fields to display (e.g., NAME,UUID,TYPE)
-h, --help: Display help information
```