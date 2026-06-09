---
title: NMAP
description: 
published: true
date: 2026-06-09T09:12:54.247Z
tags: tools
editor: markdown
dateCreated: 2026-06-09T09:12:54.247Z
---

Nmap (Network Mapper) est un outil open source incontournable pour l'exploration réseau et l'audit de sécurité. 
Concrètement, il permet de cartographier un réseau pour découvrir quels appareils y sont connectés et d'identifier les portes d'entrée (les "ports") ouvertes sur ces machines.

# L'état des ports

Lors d'une analyse, Nmap interroge les ports d'une machine (une commande de base scanne plus de 1 660 ports par défaut) et les classe dans différentes catégories. 

Voici les trois états principaux à connaître pour un débutant :

- `Open` : Une application écoute activement sur ce port et accepte les connexions. C'est souvent la cible privilégiée lors d'un audit.

- `Closed` : Le port est accessible et répond, mais aucune application ne l'utilise actuellement.

- `Filtered` : Nmap ne peut pas déterminer si le port est ouvert ou fermé car un pare-feu (ou un équipement réseau) bloque les requêtes.

# Commandes de Base

Voici les commandes les plus utiles pour commencer. 
Ouvrez votre terminal et remplacez 192.168.1.1 par l'adresse IP de votre cible.

## Scan simple d'une machine

Cette commande lance un scan standard pour trouver les ports ouverts sur une adresse IP spécifique.

```bash
nmap 192.168.1.1
```

## Scanner un réseau entier

Idéal pour voir qui est connecté à votre réseau Wi-Fi local sans analyser les ports (remplacez par votre plage réseau).

```bash
nmap -sn 192.168.1.0/24
```

## Scanner un port ou une plage de ports spécifique

Pour gagner du temps, vous pouvez cibler uniquement un port (ex: 80 pour le web) ou une plage de ports.

```bash
nmap -p 80 192.168.1.1
nmap -p 1-100 192.168.1.1
```