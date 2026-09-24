# SmartFactory MES — License Revocation List

This repository publishes a single signed data file: `crl.json`.

It contains no source code, no keys, and no customer data beyond opaque
license identifiers. The file is signed **offline** with the SmartFactory
license signing key and uploaded as a finished artifact — signing never
happens in CI, and no GitHub Action is used by this repository.

## `crl.json`

| Field | Meaning |
|-------|---------|
| `version` | Document format version |
| `issuedAt` | When this list was signed |
| `nextUpdate` | Clients treat the list as stale after this timestamp |
| `revoked[]` | Revoked license identifiers, with a reason code and timestamp |
| `signature` | RSA-2048 / SHA-256 signature over the canonical payload |

Clients verify the signature against a public key pinned inside the
application. An unreachable, unparsable or unverifiable list is treated as
"no revocation information" — never as "permitted".

Stable URL:

```
https://raw.githubusercontent.com/TsaiFisher/smartfactory-licensing/main/crl.json
```

## Reason codes

| Code | Meaning |
|------|---------|
| `terminated` | Agreement ended |
| `superseded` | Replaced by a newly issued license |
| `compromised` | License material believed to be exposed |

Questions: contact SmartFactory.
