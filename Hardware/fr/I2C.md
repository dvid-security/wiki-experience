---
title: I2C
description: 
published: true
date: 2026-06-02T08:47:06.072Z
tags: 
editor: markdown
dateCreated: 2026-06-02T08:47:06.072Z
---

Le protocole **I2C** (Inter-Integrated Circuit) est un bus de communication série synchrone largement utilisé dans les systèmes embarqués pour connecter des microcontrôleurs à des périphériques tels que des capteurs, des puces mémoire, des contrôleurs audio, des écrans, et plus encore. Développé à l'origine par **Philips** en **1982**, il est depuis devenu une norme maintenue par **NXP** et adoptée dans toute l'industrie de l'électronique.

# Architecture du bus

## Communication à deux fils

Le bus I2C utilise uniquement deux lignes de signal principales :

- **SDA** — Serial Data Line (Ligne de données série, bidirectionnelle)
- **SCL** — Serial Clock Line (Ligne d'horloge série, bidirectionnelle)

Une référence de masse commune (ground) est requise pour tous les appareils.

Les deux lignes fonctionnent en mode **drain ouvert** (ou collecteur ouvert), ce qui signifie que les appareils ne peuvent que tirer les lignes vers le niveau *bas* (low). Des résistances de tirage (pull-up resistors) maintiennent les lignes au niveau *haut* (high) lorsqu'elles sont relâchées. Ce mécanisme empêche les conflits électriques et permet à plusieurs appareils — y compris plusieurs maîtres — de partager le bus en toute sécurité.

## Topologie et adressage

I2C prend en charge :

- **Un ou plusieurs maîtres**
- **Un ou plusieurs esclaves**

Le maître initie toujours la communication et génère le signal d'horloge. Les appareils sont généralement adressés à l'aide d'**adresses sur 7 bits** (jusqu'à 128 nœuds possibles, avec certains réservés). Un modé d'**adressage sur 10 bits** existe également.

# Conditions de démarrage et d'arrêt (Start et Stop)

Chaque transaction I2C commence et se termine par des transitions de ligne spécifiques :

- **Condition de START** : SDA passe de `1 → 0` pendant que SCL reste à `1`
- **Condition de STOP** : SDA passe de `0 → 1` pendant que SCL est à `1`

Ces marqueurs permettent aux appareils de détecter quand le bus devient occupé ou libre.

# Transmission de données

## Communication basée sur l'octet

Les transferts de données s'effectuent **un octet à la fois**. Chaque octet doit être suivi d'un bit d'acquittement :

- **ACK (0)** — le récepteur confirme la réception réussie
- **NACK (1)** — indique la fin de la communication ou un appareil manquant

## Adresse + Bit de Lecture/Écriture (Read/Write)

Un transfert I2C commence par l'envoi de :

- **L'adresse de l'esclave sur 7 bits**
- **1 bit indiquant la direction** : `0` → Écriture (Write), `1` → Lecture (Read)

## Vitesses prises en charge

I2C prend en charge plusieurs débits de données standardisés :

- **Mode Standard (Standard Mode)** : 100 kbit/s
- **Mode Rapide (Fast Mode)** : 400 kbit/s
- **Mode Rapide+ (Fast Mode+)** : 1 Mbit/s
- **Mode Haute Vitesse (High-Speed Mode)** : 3,4 Mbit/s
- **Mode Ultra-Rapide (Ultra-Fast Mode)** : unidirectionnel, limité à des applications spécifiques

# Comportement électrique : Drain ouvert et Pull-Ups

Avec des sorties à drain ouvert, les appareils ne peuvent que tirer la ligne vers le bas. L'état de repos (`1`) est maintenu par des **résistances de pull-up**, généralement comprises entre **4,7 kΩ et 10 kΩ**. Cette configuration :

- évite les courts-circuits entre les appareils
- permet l'arbitrage multi-maîtres (le niveau bas est dominant)
- permet une conception de ligne partagée adaptée à de nombreux composants

---

# Séquence de communication I2C typique

Une transaction standard suit ces étapes :

1. Le maître vérifie que le bus est inactif (SDA = 1, SCL = 1).
2. Le maître émet une condition de **START**.
3. Le maître envoie **l'octet d'adresse + le bit R/W**.
4. L'esclave répond avec un **ACK**.
5. Le maître et l'esclave échangent un ou plusieurs octets.
6. Chaque octet est suivi d'un ACK/NACK.
7. Le maître envoie une condition de **STOP** pour libérer le bus.

# Applications de l'I2C

L'I2C est extrêmement courant dans l'électronique grand public et embarquée grâce à sa flexibilité et à son câblage minimal. Il est utilisé dans :

- Sur le DVID, l'écran SSD1306 est contrôlé via I2C
- Interfaces de capteurs (température, pression, centrale inertielle)
- EEPROMs et puces de mémoire série
- Modules RTC (Horloge en temps réel)
- Processeurs audio et codecs
- Pilotes d'affichage LCD / LED
- Expanseurs GPIO