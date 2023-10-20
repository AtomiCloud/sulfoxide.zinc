# sulfoxide-zinc

![Version: 1.4.0](https://img.shields.io/badge/Version-1.4.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.1.0](https://img.shields.io/badge/AppVersion-0.1.0-informational?style=flat-square)

Helm chart to deploy cluster issuers, which issuer certificate using cert-manager

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| oci://ghcr.io/atomicloud/sulfoxide.bromine | sulfoxide-bromine | 1.2.2 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| issuers | object | `{"letsencrypt":{"email":"ernest@eng.atomi.cloud","secrets":{"external":{"enable":true,"policy":{"creation":"Owner","deletion":"Retain"},"refreshInterval":"1h","remoteSecretName":"MANUAL_CLOUDFLARE_TOKEN","secretStore":{"kind":"SecretStore","name":"doppler-zinc"}},"internal":{"enable":false,"value":""},"key":"api-token","name":"cloudflare-api-token-secret"},"server":"https://acme-v02.api.letsencrypt.org/directory","solvers":[{"dns01":{"cloudflare":{"apiTokenSecretRef":{"key":"api-token","name":"cloudflare-api-token-secret"}}}}],"type":"ClusterIssuer","zones":["atomi.cloud"]}}` | Dictionary of Issuers to configure, where each key is the name of the issuer, and value is the configuration |
| issuers.letsencrypt.email | string | `"ernest@eng.atomi.cloud"` | Email to notify for the issuer |
| issuers.letsencrypt.secrets | object | `{"external":{"enable":true,"policy":{"creation":"Owner","deletion":"Retain"},"refreshInterval":"1h","remoteSecretName":"MANUAL_CLOUDFLARE_TOKEN","secretStore":{"kind":"SecretStore","name":"doppler-zinc"}},"internal":{"enable":false,"value":""},"key":"api-token","name":"cloudflare-api-token-secret"}` | Secret for DNS provider to issue certificate |
| issuers.letsencrypt.secrets.external | object | `{"enable":true,"policy":{"creation":"Owner","deletion":"Retain"},"refreshInterval":"1h","remoteSecretName":"MANUAL_CLOUDFLARE_TOKEN","secretStore":{"kind":"SecretStore","name":"doppler-zinc"}}` | External Secret, use secret from external secret store |
| issuers.letsencrypt.secrets.external.enable | bool | `true` | Enable using external secret |
| issuers.letsencrypt.secrets.external.policy | object | `{"creation":"Owner","deletion":"Retain"}` | Secret policy |
| issuers.letsencrypt.secrets.external.policy.creation | string | `"Owner"` | Creation policy |
| issuers.letsencrypt.secrets.external.policy.deletion | string | `"Retain"` | Deletion policy |
| issuers.letsencrypt.secrets.external.refreshInterval | string | `"1h"` | Refresh Interval for the external secret |
| issuers.letsencrypt.secrets.external.remoteSecretName | string | `"MANUAL_CLOUDFLARE_TOKEN"` | Remote reference for the secret |
| issuers.letsencrypt.secrets.external.secretStore | object | `{"kind":"SecretStore","name":"doppler-zinc"}` | Secret store to use |
| issuers.letsencrypt.secrets.external.secretStore.kind | string | `"SecretStore"` | Type of Secret Store: `ClusterSecretStore` or `SecretStore` |
| issuers.letsencrypt.secrets.external.secretStore.name | string | `"doppler-zinc"` | Name of secret store to use |
| issuers.letsencrypt.secrets.internal | object | `{"enable":false,"value":""}` | Internal Secret, use secret propogated via Helm |
| issuers.letsencrypt.secrets.internal.enable | bool | `false` | Enable using internal secret |
| issuers.letsencrypt.secrets.internal.value | string | `""` | The actual secret value |
| issuers.letsencrypt.secrets.key | string | `"api-token"` | Key in the secret to use |
| issuers.letsencrypt.secrets.name | string | `"cloudflare-api-token-secret"` | Name of the secret |
| issuers.letsencrypt.server | string | `"https://acme-v02.api.letsencrypt.org/directory"` | ACME compatible server |
| issuers.letsencrypt.solvers | list | `[{"dns01":{"cloudflare":{"apiTokenSecretRef":{"key":"api-token","name":"cloudflare-api-token-secret"}}}}]` | TLS Certificate solvers |
| issuers.letsencrypt.type | string | `"ClusterIssuer"` | Type of Issuer: `ClusterIssuer` or `Issuer` |
| issuers.letsencrypt.zones | list | `["atomi.cloud"]` | List zones to issue for |
| serviceTree | object | `{"layer":"1","module":"issuer","platform":"sulfoxide","service":"zinc"}` | AtomiCloud Service Tree. See [ServiceTree](https://atomicloud.larksuite.com/wiki/OkfJwTXGFiMJkrk6W3RuwRrZs64?theme=DARK&contentTheme=DARK#MHw5d76uDo2tBLx86cduFQMRsBb) |
| sulfoxide-bromine | object | `{"annotations":{"helm.sh/hook":"pre-install,pre-upgrade","helm.sh/weight":"-5"},"rootSecret":{"ref":"SULFOXIDE_ZINC"},"storeName":"doppler-zinc"}` | Create SecretStore via secret of secrets pattern |
| sulfoxide-bromine.annotations."helm.sh/hook" | string | `"pre-install,pre-upgrade"` | Helm hook to run |
| sulfoxide-bromine.annotations."helm.sh/weight" | string | `"-5"` | Helm weight to run |
| sulfoxide-bromine.rootSecret | object | `{"ref":"SULFOXIDE_ZINC"}` | Secret of Secrets reference |
| sulfoxide-bromine.rootSecret.ref | string | `"SULFOXIDE_ZINC"` | DOPPLER Token Reference |
| sulfoxide-bromine.storeName | string | `"doppler-zinc"` | Store name to create |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.1](https://github.com/norwoodj/helm-docs/releases/v1.11.1)