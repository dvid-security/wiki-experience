# Jwt_tool

`jwt_tool` is a suite of open-source tools (Python 3) designed to audit, manipulate and break JSON Web Tokens (JWTs). It enables pentesters and security engineers to :

* decode and analyse a JWT
* test for known vulnerabilities (alg=none, alg confusion, etc.),
* forge and manipulate tokens dynamically,
* carry out dictionary attacks to break the secret key.

## Main usages

1. Decoding / inspection: display JWT header and claims, including expiry date, signature, etc.
2. Security / vulnerability analysis :
    * none algorithm detection,
    * HMAC-RS/HS attack (public key used as secret),
    * exploits on corrupted claims.
3. Forging / tampering: modifying the JWT header and payload (claims, algorithms, kid, etc.) to test the robustness of the target service.
4. Key brute-force: offline dictionary or brute-force attack (several thousand words/sec).
5. Automatic sending of requests: scan an HTTP endpoint by injecting your token, via header or cookie.

## Installation

Installation is just a case of cloning the GitHub repository.

```bash
git clone https://github.com/ticarpi/jwt_tool
python3 -m pip install -r requirements.txt
```

On first run the tool will generate a config file, some utility files, logfile, and a set of Public and Private keys in various formats.

## Command line examples

This section will present some basic `jwt_tool` usages.

### Decode a JWT

This displays header, payload, time fields (exp, iat...) and validates the signature if possible.

```bash
python3 jwt_tool.py <JWT>
```

### Check a public key

Allows to validate that a public key is the good one to verify the JWT with a RSA algorithm.

```bash
python3 jwt_tool.py <JWT> -V -pk public.pem
```

### Tampering

Allows you to inject/modify header/payload fields via an interactive menu. Displays header, payload, time fields (exp, iat...) and validates the signature if possible.

```bash
python3 jwt_tool.py <JWT> -T -S <algorithm> -p <password>
```

### Known exploits

`jwt_tool` allows to perform several known attacks on JWT, like the `none` and `null` algorithms, or the key confusion between RS256 and HS256.

```bash
# None algorithm injection
python3 jwt_tool.py <JWT> -X a

# Key confusion attack
python3 jwt_tool.py <JWT> -X k -pk public_key.pub
```

### Dictionnary bruteforce attack

Since `jwt_tools` is developped in Python, this is not the most efficient way to perform a brute-force attack. In the real world, you would use a more efficient tool like `hashcat` or `john the ripper` to perform this kind of attack. However, `jwt_tool` is able to perform this attack.

```bash
python3 jwt_tool.py -C -d wordlist.txt <JWT>
```

### Automatic tests

`jwt_tool` permits to perform automatic attacks against a server by injecting multiple headers in the HTTP requests and the JWT to attemps to tamper with the JWT, and prompt the server to validate a modified JWT.

Use the `at` argument to perform all the attacks.

```bash
python3 jwt_tool.py -M at -t "https://api.example.com/endpoint" -rh "Authorization: Bearer <JWT>"
```

## Vulnerabilities covered

The following CVEs exist for JWT libraries:

* CVE-2015-9235 alg:none Attack
* CVE-2016-5431 Key Confusion Attack
* CVE-2018-0114 Key Injection Attack
* CVE-2020-28042 Null Signature Attack

Additional known attacks

* JWKS Spoofing
* "kid" Injection
* Cross-service relay attacks
* Weak secret used as a key

## Useful options

This section presents some useful `jwt_tool` options:

```
-b, --bare            return TOKENS ONLY
-t TARGETURL, --targeturl TARGETURL
                      URL to send HTTP request to with new JWT
-r REQUEST, --request REQUEST
                      URL request to base on
-rt RATE, --rate RATE
                      Max. number of requests per minute
-i, --insecure        Use HTTP for passed request
-rc COOKIES, --cookies COOKIES
                      request cookies to send with the forged HTTP request
-rh HEADERS, --headers HEADERS
                      request headers to send with the forged HTTP request (can be used multiple times for additional headers)
-pd POSTDATA, --postdata POSTDATA
                      text string that contains all the data to be sent in a POST request
-cv CANARYVALUE, --canaryvalue CANARYVALUE
                      text string that appears in response for valid token (e.g. "Welcome, ticarpi")
-np, --noproxy        disable proxy for current request (change in jwtconf.ini if permanent)
-nr, --noredir        disable redirects for current request (change in jwtconf.ini if permanent)
-M MODE, --mode MODE  Scanning mode:
                      pb = playbook audit
                      er = fuzz existing claims to force errors
                      cc = fuzz common claims
                      at - All Tests!
-X EXPLOIT, --exploit EXPLOIT
                      eXploit known vulnerabilities:
                      a = alg:none
                      n = null signature
                      b = blank password accepted in signature
                      p = 'psychic signature' accepted in ECDSA signing
                      s = spoof JWKS (specify JWKS URL with -ju, or set in jwtconf.ini to automate this attack)
                      k = key confusion (specify public key with -pk)
                      i = inject inline JWKS
-ju JWKSURL, --jwksurl JWKSURL
                      URL location where you can host a spoofed JWKS
-S SIGN, --sign SIGN  sign the resulting token:
                      hs256/hs384/hs512 = HMAC-SHA signing (specify a secret with -k/-p)
                      rs256/rs384/rs512 = RSA signing (specify an RSA private key with -pr)
                      es256/es384/es512 = Elliptic Curve signing (specify an EC private key with -pr)
                      ps256/ps384/ps512 = PSS-RSA signing (specify an RSA private key with -pr)
-pr PRIVKEY, --privkey PRIVKEY
                      Private Key for Asymmetric crypto
-T, --tamper          tamper with the JWT contents
                      (set signing options with -S or use exploits with -X)
-I, --injectclaims    inject new claims and update existing claims with new values
                      (set signing options with -S or use exploits with -X)
                      (set target claim with -hc/-pc and injection values/lists with -hv/-pv
-hc HEADERCLAIM, --headerclaim HEADERCLAIM
                      Header claim to tamper with
-pc PAYLOADCLAIM, --payloadclaim PAYLOADCLAIM
                      Payload claim to tamper with
-hv HEADERVALUE, --headervalue HEADERVALUE
                      Value (or file containing values) to inject into tampered header claim
-pv PAYLOADVALUE, --payloadvalue PAYLOADVALUE
                      Value (or file containing values) to inject into tampered payload claim
-C, --crack           crack key for an HMAC-SHA token
                      (specify -d/-p/-kf)
-d DICT, --dict DICT  dictionary file for cracking
-p PASSWORD, --password PASSWORD
                      password for cracking
-kf KEYFILE, --keyfile KEYFILE
                      keyfile for cracking (when signed with 'kid' attacks)
-V, --verify          verify the RSA signature against a Public Key
                      (specify -pk/-jw)
-pk PUBKEY, --pubkey PUBKEY
                      Public Key for Asymmetric crypto
-jw JWKSFILE, --jwksfile JWKSFILE
                      JSON Web Key Store for Asymmetric crypto
-Q QUERY, --query QUERY
                      Query a token ID against the logfile to see the details of that request
                      e.g. -Q jwttool_46820e62fe25c10a3f5498e426a9f03a
-v, --verbose         When parsing and printing, produce (slightly more) verbose output.
```