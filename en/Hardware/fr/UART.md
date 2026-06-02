---
title: UART
description: 
published: true
date: 2026-06-02T09:13:40.273Z
tags: 
editor: markdown
dateCreated: 2026-06-02T08:50:34.791Z
---

L'UART (**Universal Asynchronous Receiver-Transmitter**) est un protocole de communication matériel utilisé pour la communication série **asynchrone** entre des appareils électroniques. Contrairement au SPI et à l'I2C, qui sont des protocoles synchrones, l'UART ne nécessite pas de signal d'horloge. Au lieu de cela, il utilise un débit en bauds prédéfini (baud rate) pour synchroniser la transmission de données.

L'UART est couramment utilisé dans les systèmes embarqués, les microcontrôleurs et les modules de communication tels que les modules GPS, Bluetooth et Wi-Fi.

# Comment fonctionne l'UART

L'UART permet une communication bidirectionnelle entre deux appareils sur deux fils :

- `TX` (Transmission) : Envoie des données.
- `RX` (Réception) : Reçoit des données.

La ligne TX de chaque appareil est connectée à la ligne RX de l'autre appareil.

Contrairement aux protocoles synchrones, l'UART n'utilise pas de signal d'horloge. Au lieu de cela, les deux appareils s'accordent sur un débit en bauds commun (vitesse de transmission de données). Les données sont transmises un bit à la fois dans un format structuré.

Chaque transmission UART se compose d'une trame (frame) qui comprend :

- Bit de démarrage (Start Bit, 1 bit) : Un 0 (basse tension) est envoyé pour indiquer le début de la transmission des données.
- Bits de données (Data Bits, 5 à 9 bits, généralement 8 bits) : Les données réelles en cours de transmission.
- Bit de parité (Parity Bit, 1 bit, optionnel) : Utilisé pour la détection d'erreurs (parité paire ou impaire).
- Bit(s) d'arrêt (Stop Bit, 1 à 2 bits) : Un 1 (haute tension) pour signaler la fin de la transmission.

Le débit en bauds définit la vitesse de transmission en bits par seconde (bps). Les débits en bauds courants incluent :

- 9600 bps (par défaut pour de nombreux appareils)
- 115200 bps (couramment utilisé pour une communication rapide)
- 57600, 38400, 19200, 4800 bps, etc.

**Les deux appareils doivent utiliser le même débit en bauds pour communiquer correctement.**

# Caractéristiques de l'UART

Voici quelques fonctionnalités intéressantes et avancées de l'UART :

- **DMA (Direct Memory Access / Accès direct à la mémoire)** : Réduit la charge du processeur en gérant automatiquement les transferts de données volumineux.
- **Contrôle de flux matériel (Hardware Flow Control - RTS/CTS)** : Des signaux supplémentaires de demande d'envoi (Request to Send - RTS) et de prêt à envoyer (Clear to Send - CTS) empêchent les débordements de tampon (buffer overflows).
- **Mode Semi-duplex (Half-Duplex)** : Utilise un seul fil pour la communication bidirectionnelle (une direction à la fois).
- **UART logiciel (Software Serial / Bit-Banging)** : Permet l'émulation UART sur des microcontrôleurs sans matériel UART dédié.

# L'UART dans l'utilisation quotidienne

- **Systèmes embarqués** : Communication entre microcontrôleurs (par ex., Arduino, Raspberry Pi, ESP32).
- **Modules GPS** : Transmission des données de localisation via UART.
- **Modules Bluetooth (HC-05, HC-06)** : Communication série avec des appareils sans fil.
- **Débogage & Surveillance série** : Utilisé pour le débogage avec des outils comme le moniteur série (Serial Monitor) d'Arduino.
- **Applications industrielles** : Communication avec des capteurs, des contrôleurs de moteur et d'autres périphériques.