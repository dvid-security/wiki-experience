---
title: MQTT
description: 
published: true
date: 2026-06-02T08:32:54.682Z
tags: 
editor: markdown
dateCreated: 2026-06-02T08:32:37.642Z
---

MQTT (**Message Queuing Telemetry Transport**) est un protocole de messagerie léger de type publication-abonnement (publish-subscribe) conçu pour les appareils limités et les réseaux à faible bande passante, à latence élevée ou peu fiables. Il est largement utilisé dans les applications de l'Internet des objets (IoT) pour une communication efficace entre les capteurs, les appareils et les serveurs.

Développé à l'origine en 1999 par IBM, MQTT est devenu un protocole populaire pour l'IoT en raison de sa simplicité, de ses faibles exigences en ressources et de sa prise en charge de la messagerie en temps réel.

# Versions de MQTT

MQTT a subi plusieurs mises à jour pour améliorer ses fonctionnalités et sa sécurité :

- MQTT 3.1 (2010) : La première version largement adoptée, introduisant des fonctionnalités clés comme la QoS.
- MQTT 3.1.1 (2014) : Amélioration de l'interopérabilité et clarification des spécifications.
- MQTT 5.0 (2019) : A introduit des améliorations majeures, telles que :
    - Propriétés définies par l'utilisateur pour les métadonnées personnalisées.
    - Accusés de réception négatifs (NACK) pour les messages rejetés.
    - Amélioration du signalement des erreurs et de l'évolutivité.

# Comment fonctionne MQTT

MQTT fonctionne sur un modèle publication-abonnement, différent du modèle client-serveur traditionnel des protocoles comme HTTP. Au lieu d'une connexion directe entre les appareils, MQTT s'appuie sur un courtier (broker) central pour gérer la communication.

## Composants clés

MQTT fonctionne avec 3 composants clés :

- Courtier (Broker) : Le serveur central qui achemine les messages entre les appareils. Des exemples de courtiers incluent Eclipse Mosquitto, HiveMQ et AWS IoT Core.
- Clients : Appareils ou applications qui se connectent au courtier. Les clients peuvent :
    - Publier des messages sur des sujets (topics).
    - S'abonner à des sujets pour recevoir des messages.
- Sujets (Topics) : Les messages sont classés en sujets (par ex., home/temperature) pour organiser la communication. Les clients s'abonnent à ces sujets pour recevoir des données pertinentes et peuvent publier sur des sujets.

Généralement, MQTT fonctionne sur TCP mais il prend également en charge WebSocket. Les ports par défaut sont le 1883 (**non chiffré**) et le 8883 (TLS **chiffré**).

De la même manière que HTTP, un mécanisme **Keep-Alive** garantit que les clients restent connectés au courtier.

## Flux de travail (Workflow)

Le flux de travail MQTT est divisé en 3 phases :

1. Un client publie un message sur un sujet (par ex., home/livingroom/temperature).
2. Le courtier reçoit le message et le transmet à tous les clients qui se sont abonnés à ce sujet.
3. Les clients abonnés reçoivent le message en temps réel.

Voici un exemple simple d'un flux de travail MQTT :

1. Un capteur de température publie des données sur le sujet home/livingroom/temperature, et une application mobile s'abonne au même sujet pour afficher les mises à jour de température.
2. Le capteur envoie un message : {"temperature": 22.5} au courtier. Le courtier transmet le message à tous les abonnés du sujet et l'application mobile reçoit le message et met à jour l'interface utilisateur.
3. L'application mobile peut publier des commandes (par ex., 	urn_off) sur un sujet tel que home/livingroom/thermostat/command, auquel le thermostat est abonné.

# Caractéristiques de MQTT

Voici les principales fonctionnalités et caractéristiques de MQTT :

- **Léger et Efficace** : Conçu pour les appareils ayant une puissance de traitement et une mémoire limitées, MQTT utilise une bande passante minimale.
- **Modèle Publication-Abonnement** : Découple les expéditeurs de messages (éditeurs) des destinataires (abonnés), améliorant ainsi l'évolutivité.
- **Qualité de service (QoS)** : MQTT garantit une livraison fiable des messages avec trois niveaux de QoS :
    - QoS 0 : Livraison "Au plus une fois". Les messages sont envoyés sans confirmation.
    - QoS 1 : Livraison "Au moins une fois". Les messages sont envoyés jusqu'à ce qu'ils soient acquittés par le destinataire.
    - QoS 2 : Livraison "Exactement une fois". Garantit que le message n'est reçu qu'une seule fois, même en cas de doublons.
- **Messages conservés (Retained Messages)** : Un message publié peut être conservé par le courtier, permettant aux nouveaux abonnés de recevoir immédiatement le message le plus récent.
- **Messages de testament (Will Messages)** : Permet aux clients de définir un message de "dernier testament" que le courtier envoie si le client se déconnecte de façon inattendue.
- **Sessions persistantes** : Prend en charge les sessions client persistantes, permettant une reconnexion sans perdre l'abonnement ou l'état du message.
- **Sécurité** : Bien que MQTT lui-même n'impose pas la sécurité, le chiffrement (via TLS) et l'authentification (via nom d'utilisateur/mot de passe ou certificats) sont couramment utilisés.

# Considérations de sécurité avec MQTT

Étant donné que MQTT est couramment utilisé dans l'IoT, la sécurité est une préoccupation majeure. Les pratiques de sécurité standard incluent :

- **Chiffrement** : Utiliser TLS/SSL pour chiffrer les messages, garantissant ainsi la confidentialité.
- **Authentification** : Nom d'utilisateur/mot de passe pour une authentification de base et certificats pour une authentification TLS mutuelle.
- **Contrôle d'accès** : Les courtiers peuvent appliquer des autorisations au niveau du sujet, garantissant que les clients ne peuvent publier/s'abonner qu'aux sujets autorisés.
- **Pare-feu (Firewalls)** : Restreindre la communication MQTT aux plages d'adresses IP et aux ports approuvés.

# MQTT dans l'utilisation quotidienne

MQTT est idéal pour les scénarios où l'efficacité et la fiabilité sont essentielles, en particulier dans les environnements IoT :

- **Appareils IoT et pour la maison intelligente (Smart Home)** :
    - Communication de données de capteurs (par ex., température, humidité).
    - Contrôle des appareils (par ex., allumer les lumières ou régler les thermostats).
- **IoT Industriel (IIoT)** :
    - Surveillance de l'état et des performances des équipements.
    - Envoi d'alertes en temps réel pour les machines.
- **Véhicules connectés** :
    - Échange de données entre les véhicules et les serveurs (par ex., GPS, vitesse).
    - Systèmes de gestion de flotte.
- **Santé (Healthcare)** :
    - Appareils portables transmettant les données des patients (par ex., fréquence cardiaque, tension artérielle).
    - Surveillance à distance de l'équipement médical.
- **Énergie et services publics** :
    - Réseaux électriques intelligents pour la surveillance de la consommation d'énergie.
    - Communication entre les panneaux solaires et les systèmes centraux.
