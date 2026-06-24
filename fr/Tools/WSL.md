---
title: WSL
description: 
published: true
date: 2026-06-24T08:53:32.074Z
tags: 
editor: markdown
dateCreated: 2026-06-24T08:53:32.073Z
---

# Installation de Kali WSL

Installer Kali sous WSL plutôt qu’en VM permet d’avoir un environnement Linux plus léger, plus rapide à lancer et mieux intégré à Windows pour les usages quotidiens. De plus pour les utilisateur Windows ARM (Snapdragon), il n’est pas encore possible de créer des VMs.

---

Aller sur le Microsoft Store, chercher Kali Linux et l’installer

![image.png](/files/wsl/image.png)

Une fois installé, on peux accéder au fichier dans le gestionnaire de fichier Windows :

![image2.png](/files/wsl/image2.png)
![image3.png](/files/wsl/image3.png)

---

A noter que si vous préférez, vous pouvez installer d’autre distribution Linux tel que Debian, Ubuntu, ect…

# Partage USB

Pour avoir un périphérique branché sur notre PC sur une machine WSL (ex : kali), il est nécessaire d’utiliser `usbipd` . Toutes les commande sont à effectuer sur un powershell lancé en tant qu’administrateur.

**Installer usbipd :**

```powershell
winget install usbipd
```

**Lister les périphérique :**

```powershell
usbipd list
```

Noter le BUSID du périphérique (ex 1-2) : 

```powershell
1-2    10c4:ea60  CP2102 USB to UART Bridge Controller        Not shared
```

**Lier le périphérique sur WSL :**

```powershell
usbipd bind --busid 1-2
usbipd attach --wsl --busid 1-2
```

---

A noter qu’à chaque fois que vous redémarrez votre PC, fermez WSL, ou même débranchez/rebranchez physiquement votre périphérique, il faudra a nouveau exécuter `usbipd attach` .