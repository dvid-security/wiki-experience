---
title: Découvrir la carte DVID
description: 
published: true
date: 2026-06-02T09:12:58.549Z
tags: 
editor: markdown
dateCreated: 2026-06-02T07:47:41.229Z
---

Sur la carte DVID, vous pouvez identifier deux types de connecteurs de programmation. Le premier est le JTAG. Cette méthode de programmation avancée permet un accès direct à la mémoire et aux registres des composants.

![jtagconnectors.png](/files/discover/jtagconnectors.png)

La seconde méthode de programmation consiste à utiliser le port UART. La carte peut être configurée en mode téléchargement, ce qui permet le transfert et l'installation d'un firmware.

![uartconnectors.png](/files/discover/uartconnectors.png)

L'étape suivante consiste à câbler correctement le dongle UART pour permettre le transfert d'informations et l'installation du firmware. Vous pouvez placer les cavaliers sur le dongle UART en suivant les captures d'écran ci-dessous. Les couleurs n'ont pas d'importance ; il suffit qu'elles soient identiques de chaque côté du fil :

- VCC / +5V : alimentation de la carte

- GND : alimentation de la carte

- RX : réception des informations UART sur le dongle

- TX : transmission des informations UART depuis le dongle

![uartdongle.jpg](/files/discover/uartdongle.jpg)

Sur la carte, vous pouvez identifier les ports d'alimentation, TX et RX. L'alimentation peut être câblée conformément aux captures d'écran suivantes :

- Adaptateur VCC/+5V à +V sur la carte

- Adaptateur GND à GND sur la carte

![powerwireonboard.jpg](/files/discover/powerwireonboard.jpg)

Sur le connecteur UART, les fils doivent être croisés. En effet, l'UART est le seul protocole où les fils sont croisés. N'oubliez pas cette manipulation.

- Adaptateur TX à RX sur la carte

- Adaptateur RX à TX sur la carte

![uartwireonboard.jpg](/files/discover/uartwireonboard.jpg)