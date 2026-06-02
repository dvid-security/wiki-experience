---
title: HTTP
description: 
published: true
date: 2026-06-02T11:44:22.598Z
tags: 
editor: markdown
dateCreated: 2026-06-02T11:44:22.598Z
---

Le **Hypertext Transfer Protocol** (HTTP) est un protocole fondamental du World Wide Web, permettant la communication entre les clients (tels que les navigateurs web) et les serveurs. C'est un protocole de la couche application conçu pour la transmission de documents hypermédias, tels que HTML, des images et des vidéos. HTTP suit un modèle requête-réponse, où les clients envoient des requêtes, et les serveurs renvoient des réponses.

HTTP est sans état (stateless), ce qui signifie que chaque requête d'un client à un serveur est traitée de manière indépendante, sans mémoire des interactions précédentes à moins qu'elles ne soient explicitement gérées à l'aide de mécanismes tels que les cookies ou le stockage de session.

# Versions de HTTP

Voici les différentes versions de HTTP avec leurs dates de sortie :

- HTTP/0.9 (1991) : La première version, axée sur le transfert de contenu HTML brut. Ne prenait en charge que les requêtes GET et manquait d'en-têtes ou de métadonnées.
- HTTP/1.0 (1996) : Introduction des métadonnées (en-têtes), prise en charge des méthodes POST et HEAD, et des codes d'état. Chaque requête nécessitait une connexion TCP distincte.
- HTTP/1.1 (1997) : Introduction des connexions persistantes (keep-alive), de l'encodage de transfert en blocs (chunked transfer encoding) et du pipelining. Est devenue la version la plus largement utilisée pendant des décennies.
- HTTP/2 (2015) : Axée sur l'amélioration des performances, comme le multiplexage (envoi de requêtes multiples sur une seule connexion), la compression des en-têtes, et la priorisation.
- HTTP/3 (2020) : S'appuie sur HTTP/2 mais remplace TCP par QUIC, un protocole basé sur UDP, pour réduire la latence et améliorer la résilience de la connexion.

# Comment fonctionne HTTP

HTTP fonctionne sur un modèle client-serveur :

- Client : Initie la communication en envoyant une requête HTTP. Exemples : Navigateurs web (par ex. Chrome, Firefox), applications mobiles, ou clients API.
- Serveur : Traite la requête et renvoie une réponse HTTP contenant la ressource demandée ou un message d'erreur.

## Composants clés d'une requête HTTP

Une **requête HTTP** se compose de :

- Ligne de requête : Spécifie la méthode HTTP, la ressource cible (URL) et la version du protocole (par ex., `GET /index.html HTTP/1.1`).
- En-têtes : Métadonnées concernant la requête (par ex., `User-Agent, Host, Accept`).
- Corps (Body) : (Optionnel) Contient des données envoyées avec la requête, telles que des soumissions de formulaires ou des charges utiles JSON.

## Composants clés d'une réponse HTTP

Une **réponse HTTP** se compose de :

- Ligne de statut : Indique la version du protocole, le code d'état et le message de statut (par ex., `HTTP/1.1 200 OK`).
- En-têtes : Métadonnées concernant la réponse (par ex., `Content-Type, Content-Length, Server`).
- Corps (Body) : Le contenu renvoyé (par ex., HTML, JSON, ou images).

## Méthodes HTTP

HTTP définit plusieurs méthodes pour différents types d'actions :

- `GET` : Récupère des données d'un serveur.
- `POST` : Soumet des données à un serveur pour traitement (par ex., données de formulaire).
- `PUT` : Met à jour ou remplace une ressource sur le serveur.
- `DELETE` : Supprime une ressource sur le serveur.
- `HEAD` : Similaire à `GET` mais ne récupère que les en-têtes, pas le corps.
- `OPTIONS` : Décrit les options de communication pour la ressource cible.
- `PATCH` : Met à jour partiellement une ressource sur le serveur.
- `TRACE` : Fait écho à la requête reçue à des fins de diagnostic.
- `CONNECT` : Établit un tunnel pour la communication, souvent utilisé avec HTTPS.

## Codes d'état HTTP

HTTP utilise des codes d'état standardisés pour indiquer le résultat d'une requête :

- 1xx : **Informationnel**
    - 100 Continue : Requête reçue, continuez à envoyer.
    - 101 Switching Protocols : Le serveur passe à un nouveau protocole.
- 2xx : **Succès**
    - 200 OK : La requête a réussi.
    - 201 Created : La ressource a été créée avec succès.
    - 204 No Content : La requête a réussi, aucun contenu n'est renvoyé.
- 3xx : **Redirection**
    - 301 Moved Permanently : La ressource a une nouvelle URL permanente.
    - 302 Found : Redirection temporaire.
    - 304 Not Modified : La ressource n'a pas été modifiée depuis la dernière demande.
- 4xx : **Erreurs client**
    - 400 Bad Request : Syntaxe de requête invalide.
    - 401 Unauthorized : Authentification requise.
    - 403 Forbidden : L'accès à la ressource est refusé.
    - 404 Not Found : Ressource non trouvée.
- 5xx : **Erreurs serveur**
    - 500 Internal Server Error : Le serveur a rencontré une erreur.
    - 502 Bad Gateway : Réponse invalide d'un serveur en amont.
    - 503 Service Unavailable : Le serveur est temporairement indisponible.

## Caractéristiques de HTTP

Voici les principales caractéristiques de HTTP :

- **Sans état (Statelessness)** : HTTP ne conserve aucune information de session, ce qui simplifie la conception du protocole. Cependant, cela nécessite des mécanismes comme des cookies ou des jetons pour la gestion de session.
- **Gestion de contenu flexible** : HTTP prend en charge divers types de contenu (par ex., HTML, JSON, XML, images, vidéos) via l'en-tête Content-Type.
- **Extensibilité** : Des en-têtes et des méthodes personnalisés peuvent être ajoutés pour prendre en charge de nouvelles fonctionnalités.
- **Sécurité (HTTPS)** : HTTPS est la version sécurisée de HTTP qui utilise SSL/TLS pour chiffrer la communication, garantissant ainsi la confidentialité, l'intégrité et l'authentification.

# HTTP dans l'utilisation quotidienne

Comme déjà mentionné, le protocole HTTP est largement utilisé sur le web. Voici quelques exemples d'utilisation :

- **Navigation web** : Les navigateurs utilisent HTTP pour récupérer et afficher des pages web.
- **APIs** : Les API RESTful s'appuient sur HTTP pour la communication entre les clients et les serveurs. **Ceci sera particulièrement exploré dans les formations cloud.**
- **Téléchargements de fichiers** : De nombreux services de transfert de fichiers utilisent HTTP comme protocole sous-jacent.
- **Appareils IoT** : Les appareils connectés à Internet utilisent souvent HTTP pour envoyer et recevoir des données. **Ceci sera particulièrement exploré dans les formations.**