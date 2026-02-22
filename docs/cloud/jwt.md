
# Understanding JWT (JSON Web Tokens)

**JSON Web Tokens (JWT)** are a compact, URL‑safe mechanism for securely transmitting information between two parties. They are widely used in modern applications for authentication, authorization, and information exchange, and are defined by the open standard RFC 7519.

JWTs ensure integrity and authenticity using digital signatures generated with HMAC secrets or public/private key pairs such as RSA or ECDSA.

---

# 1. Why JWTs Exist

As applications evolved into distributed systems and microservice architectures, maintaining centralized server-side sessions became difficult. JWT enables **stateless authentication**, allowing clients to store tokens and send them with each request while servers validate them without keeping session data.

JWT is ideal for:
- APIs
- Mobile applications
- Single‑Page Applications (SPAs)
- Microservices

---

# 2. Structure of a JWT

A JWT consists of **three Base64URL‑encoded parts** separated by dots:
```
header.payload.signature
```

## 2.1 Header
Contains metadata:
- `alg` – signing algorithm (e.g., HS256, RS256)
- `typ` – token type (JWT)

Example:
```json
{ "alg": "HS256", "typ": "JWT" }
```

## 2.2 Payload
Contains **claims** such as user ID, expiration, issuer, etc. Common claims:
- `iss` – issuer
- `sub` – subject
- `aud` – audience
- `exp` – expiration time
- `iat` – issued at

## 2.3 Signature
Ensures data integrity:
```
HMACSHA256(base64UrlEncode(header) + "." + base64UrlEncode(payload), secret)
```


---

# 3. How JWT Authentication Works

1. User logs in and sends credentials.
2. Server validates them.
3. Server generates a signed JWT.
4. Client stores the token locally.
5. Client sends token in `Authorization: Bearer <token>` header.
6. Server verifies signature and expiration.
7. Access is granted if valid.
---

# 4. Types of JWT

## JWS – JSON Web Signature
Signed but **not encrypted**; payload is readable but tamper‑proof.

## JWE – JSON Web Encryption
Encrypted payload, ensuring confidentiality.

---

# 5. When to Use JWT

### Authorization
Once authenticated, clients include the JWT in each request to access permitted resources. It is widely used for SSO (Single Sign‑On).

### Information Exchange
Digitally signed tokens ensure data authenticity and tamper‑resistance.

---

# 6. Security Considerations

### Risks
- No built‑in revocation → requires denylist.
- Payload is visible unless JWE is used.
- Stolen tokens allow impersonation until expiration.

### Best Practices
- Use HTTPS.
- Set short expiration (`exp`).
- Use refresh tokens for long sessions.
- Avoid sensitive data in payload.
- Protect signing keys; use strong algos (RS256).
---
