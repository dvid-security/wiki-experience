---
title: JWT
description: 
published: true
date: 2026-06-02T08:29:59.172Z
tags: 
editor: markdown
dateCreated: 2026-06-02T08:29:43.276Z
---

Les **JSON Web Tokens (JWT)** sont un mécanisme compact et sécurisé pour les URL, permettant de transmettre des informations en toute sécurité entre deux parties. Ils sont largement utilisés dans les applications modernes pour l'authentification, l'autorisation et l'échange d'informations, et sont définis par la norme ouverte RFC 7519.

Les JWT garantissent l'intégrité et l'authenticité à l'aide de signatures numériques générées avec des secrets HMAC ou des paires de clés publique/privée telles que RSA ou ECDSA.

# Pourquoi les JWT existent-ils

Au fur et à mesure que les applications ont évolué vers des systèmes distribués et des architectures de microservices, le maintien de sessions centralisées côté serveur est devenu difficile. JWT permet une **authentification sans état (stateless)**, autorisant les clients à stocker des jetons et à les envoyer avec chaque requête tandis que les serveurs les valident sans conserver de données de session.

JWT est idéal pour :

- Les APIs - Applications mobiles
- Les applications à page unique (SPAs)
- Les microservices

# Structure d'un JWT

Un JWT se compose de **trois parties encodées en Base64URL** séparées par des points :

- `header.payload.signature`

## En-tête (Header)

Contient les métadonnées :

- "alg" : algorithme de signature (par ex., HS256, RS256)
- "typ" : type de jeton (JWT)

Exemple :

```json
{ "alg": "HS256", "typ": "JWT" }
```

## Charge utile (Payload)

Contient des **revendications (claims)** telles que l'ID utilisateur, l'expiration, l'émetteur (issuer), etc. Revendications courantes :

- `iss` : émetteur (issuer)
- `sub` : sujet (subject)
- `aud` : audience
- `exp` : délai d'expiration (expiration time)
- `iat` : émis à (issued at)

## Signature

Garantit l'intégrité des données :

```	ext
HMACSHA256(base64UrlEncode(header) + "." + base64UrlEncode(payload), secret)
```

# Comment fonctionne l'authentification JWT

1. L'utilisateur se connecte et envoie ses identifiants.
2. Le serveur les valide.
3. Le serveur génère un JWT signé.
4. Le client stocke le jeton localement.
5. Le client envoie le jeton dans l'en-tête "Authorization: Bearer \<token>".
6. Le serveur vérifie la signature et l'expiration.
7. L'accès est accordé s'il est valide.

# Types de JWT

## JWS – JSON Web Signature

Signé mais **non chiffré** ; la charge utile est lisible mais infalsifiable.

## JWE – JSON Web Encryption

Charge utile chiffrée, garantissant la confidentialité.

# Quand utiliser JWT

## Autorisation

Une fois authentifiés, les clients incluent le JWT dans chaque requête pour accéder aux ressources autorisées. Il est largement utilisé pour le SSO (Single Sign-On / Authentification unique).

## Échange d'informations

Les jetons signés numériquement garantissent l'authenticité et la résistance à la falsification des données.

# Considérations de sécurité

## Risques

- Pas de révocation intégrée → nécessite une liste de refus (denylist).
- La charge utile est visible à moins d'utiliser JWE.
- Les jetons volés permettent l'usurpation d'identité jusqu'à leur expiration.

## Bonnes pratiques

- Utiliser HTTPS.
- Définir une expiration courte ("exp").
- Utiliser des jetons de rafraîchissement (refresh tokens) pour les longues sessions.
- Éviter les données sensibles dans la charge utile.
- Protéger les clés de signature ; utiliser des algorithmes forts (RS256).
