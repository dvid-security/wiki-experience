---
title: WSL
description: 
published: true
date: 2026-06-24T08:55:41.341Z
tags: 
editor: markdown
dateCreated: 2026-06-24T08:55:41.341Z
---

# Installing Kali WSL

Installing Kali under WSL rather than in a VM provides a lighter Linux environment that is faster to launch and better integrated with Windows for daily use. Furthermore, for Windows ARM (Snapdragon) users, it is not yet possible to create VMs.

---

Go to the Microsoft Store, search for Kali Linux, and install it

![image.png](/files/wsl/image.png)

Once installed, you can access the files in the Windows file manager:

![image2.png](/files/wsl/image2.png)
![image3.png](/files/wsl/image3.png)

---

Note that if you prefer, you can install other Linux distributions such as Debian, Ubuntu, etc.

# USB Sharing

To make a device plugged into your PC available on a WSL machine (e.g., Kali), it is necessary to use `usbipd`. All commands must be executed in a PowerShell session launched as an administrator.

**Install usbipd:**

```powershell
winget install usbipd
```

**List the devices:**

```powershell
usbipd list
```

Note the BUSID of the device (e.g., 1-2): 

```powershell
1-2    10c4:ea60  CP2102 USB to UART Bridge Controller        Not shared
```

**Bind the device to WSL:**

```powershell
usbipd bind --busid 1-2
usbipd attach --wsl --busid 1-2
```

---

Note that each time you restart your PC, close WSL, or even physically unplug/replug your device, you will need to execute `usbipd attach` again.