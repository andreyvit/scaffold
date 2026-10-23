# Store configuration in JSON

All configuration is inside config.json, in top-level package or similar, per environment or env group (app-environments.md):

```json
{
  "all": {
    "RolloutNewSuperFeature": true,
  },
  "all-local": {
  },
  "production": {
    "HTTPPort": 3001,
    "WorkerCount": 50,
    "RolloutNewSuperFeature": false,
    "ConfigOverridesPath": "/srv/excellentd-production/excellent-production.json",
    "ConfigOverridesPathRequired": true,
    "SecretKeyringPath": "/srv/excellentd-production/keyring",
  },
  "staging": {
    "HTTPPort": 3002,
    "WorkerCount": 20,
    "ConfigOverridesPath": "/srv/excellentd-staging/excellent-staging.json",
    "ConfigOverridesPathRequired": true,
    "SecretKeyringPath": "/srv/excellentd-staging/keyring",
  },
  "development": {
    "HTTPPort": 3001,
    "WorkerCount": 5,
    "ConfigOverridesPath": "config-local.json",
    "SecretKeyringPath": ".keyring",
  },
  "testing": {
    "HTTPPort": 3002,
    "WorkerCount": 2,
  },
}
```

(Use names appropriate for web stack; these are examples for Go.)

Read sections for each group and environment itself into same object, so that later values overwrite earlier ones. If ConfigOverridesPath non-empty, read it last, so that it overrides anything else. `config-local.json. If ConfigOverridesPathRequired, then crash if ConfigOverridesPath empty or not found to prevent mistakes.

No env vars or cmdline options for config, use JSON only.

Secrets in JSON encrypted using NaCl-compatible secretbox encryption (XSalsa20 + Poly1305) via golang.org/x/crypto/nacl/secretbox. Each value is "<keyname>:<base64>", where <keyname> is looked up in the configured keyring file. Keyring uses keyname=hex format. Create key `default` by default; user will add more keys as needed. Add `-encrypt-secret <keyname>` cmdline arg which reads secret from stdin, strips leading/trailing whitespace, encrypts and prints.

Use JSON parser that allows trailing commas and comments if you can; in Go use jsonfix.
