# sulfoxide-zinc

![Version: 1.10.0](https://img.shields.io/badge/Version-1.10.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.6.0](https://img.shields.io/badge/AppVersion-1.6.0-informational?style=flat-square)

Helm chart to deploy cluster issuers, which issuer certificate using cert-manager

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| oci://ghcr.io/atomicloud/sulfoxide.bromine | sulfoxide-bromine | 1.6.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| issuers | object | `{"letsencrypt":{"email":"ernest@eng.atomi.cloud","secrets":{"external":{"enable":true,"policy":{"creation":"Owner","deletion":"Retain"},"refreshInterval":"1h","remoteSecretName":"CLOUDFLARE_TOKEN","secretStore":{"kind":"SecretStore","name":"zinc"}},"internal":{"enable":false,"value":""},"key":"api-token","name":"cloudflare-api-token-secret"},"server":"https://acme-v02.api.letsencrypt.org/directory","solvers":[{"dns01":{"cloudflare":{"apiTokenSecretRef":{"key":"api-token","name":"cloudflare-api-token-secret"}}}}],"type":"ClusterIssuer","zones":["atomi.cloud"]}}` | Dictionary of Issuers to configure, where each key is the name of the issuer, and value is the configuration |
| issuers.letsencrypt.email | string | `"ernest@eng.atomi.cloud"` | Email to notify for the issuer |
| issuers.letsencrypt.secrets | object | `{"external":{"enable":true,"policy":{"creation":"Owner","deletion":"Retain"},"refreshInterval":"1h","remoteSecretName":"CLOUDFLARE_TOKEN","secretStore":{"kind":"SecretStore","name":"zinc"}},"internal":{"enable":false,"value":""},"key":"api-token","name":"cloudflare-api-token-secret"}` | Secret for DNS provider to issue certificate |
| issuers.letsencrypt.secrets.external | object | `{"enable":true,"policy":{"creation":"Owner","deletion":"Retain"},"refreshInterval":"1h","remoteSecretName":"CLOUDFLARE_TOKEN","secretStore":{"kind":"SecretStore","name":"zinc"}}` | External Secret, use secret from external secret store |
| issuers.letsencrypt.secrets.external.enable | bool | `true` | Enable using external secret |
| issuers.letsencrypt.secrets.external.policy | object | `{"creation":"Owner","deletion":"Retain"}` | Secret policy |
| issuers.letsencrypt.secrets.external.policy.creation | string | `"Owner"` | Creation policy |
| issuers.letsencrypt.secrets.external.policy.deletion | string | `"Retain"` | Deletion policy |
| issuers.letsencrypt.secrets.external.refreshInterval | string | `"1h"` | Refresh Interval for the external secret |
| issuers.letsencrypt.secrets.external.remoteSecretName | string | `"CLOUDFLARE_TOKEN"` | Remote reference for the secret |
| issuers.letsencrypt.secrets.external.secretStore | object | `{"kind":"SecretStore","name":"zinc"}` | Secret store to use |
| issuers.letsencrypt.secrets.external.secretStore.kind | string | `"SecretStore"` | Type of Secret Store: `ClusterSecretStore` or `SecretStore` |
| issuers.letsencrypt.secrets.external.secretStore.name | string | `"zinc"` | Name of secret store to use |
| issuers.letsencrypt.secrets.internal | object | `{"enable":false,"value":""}` | Internal Secret, use secret propogated via Helm |
| issuers.letsencrypt.secrets.internal.enable | bool | `false` | Enable using internal secret |
| issuers.letsencrypt.secrets.internal.value | string | `""` | The actual secret value |
| issuers.letsencrypt.secrets.key | string | `"api-token"` | Key in the secret to use |
| issuers.letsencrypt.secrets.name | string | `"cloudflare-api-token-secret"` | Name of the secret |
| issuers.letsencrypt.server | string | `"https://acme-v02.api.letsencrypt.org/directory"` | ACME compatible server |
| issuers.letsencrypt.solvers | list | `[{"dns01":{"cloudflare":{"apiTokenSecretRef":{"key":"api-token","name":"cloudflare-api-token-secret"}}}}]` | TLS Certificate solvers |
| issuers.letsencrypt.type | string | `"ClusterIssuer"` | Type of Issuer: `ClusterIssuer` or `Issuer` |
| issuers.letsencrypt.zones | list | `["atomi.cloud"]` | List zones to issue for |
| secretAnnotation | object | `{"argocd.argoproj.io/sync-wave":"-2"}` | Secret Annotations (External Secrets) to control synchronization |
| serviceTree | object | `{"layer":"1","module":"issuer","platform":"sulfoxide","service":"zinc"}` | AtomiCloud Service Tree. See [ServiceTree](https://atomicloud.larksuite.com/wiki/OkfJwTXGFiMJkrk6W3RuwRrZs64?theme=DARK&contentTheme=DARK#MHw5d76uDo2tBLx86cduFQMRsBb) |
| sulfoxide-bromine | object | `{"annotations":{"argocd.argoproj.io/sync-wave":"-3"},"rootSecret":{"name":"zinc","ref":{"clientId":"SULFOXIDE_ZINC_CLIENT_ID","clientSecret":"SULFOXIDE_ZINC_CLIENT_SECRET"}},"serviceTree":{"platform":"sulfoxide","service":"zinc"},"storeName":"zinc"}` | Create SecretStore via secret of secrets pattern |
| sulfoxide-bromine.rootSecret | object | `{"name":"zinc","ref":{"clientId":"SULFOXIDE_ZINC_CLIENT_ID","clientSecret":"SULFOXIDE_ZINC_CLIENT_SECRET"}}` | Secret of Secrets reference |
| sulfoxide-bromine.rootSecret.ref | object | `{"clientId":"SULFOXIDE_ZINC_CLIENT_ID","clientSecret":"SULFOXIDE_ZINC_CLIENT_SECRET"}` | DOPPLER Token Reference |
| sulfoxide-bromine.storeName | string | `"zinc"` | Store name to create |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
