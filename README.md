# dsb-messagebroker

![Version: 1.2.0](https://img.shields.io/badge/Version-1.2.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.3.0](https://img.shields.io/badge/AppVersion-0.3.0-informational?style=flat-square)

A Helm chart for Kubernetes


## Introduction
This is a repository with helm chart for DSB Messagebroker application.

For more information about DSB Client Gateway please check the [repository](https://github.com/energywebfoundation/dsb).


## Quickstart

```
minikube start

create a secret with JWT_SECRET and PRIVATE_KEY (blueprint below)

apiVersion: v1
kind: Secret
metadata:
    name: dsb-messagebroker-test-secret
type: Opaque
data:
    privateKey: base64(PRIVATE_KEY)
    jwtSecret: base64(JWT_SECRET)

kubectl apply -f secret.yaml

helm install dsb-messagebroker-test https://github.com/energywebfoundation/dsb-messagebroker-helm/archive/refs/tags/v1.0.2.tar.gz

kubectl get pods
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| fullnameOverride | string | `"dsb-messagebroker"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"aemocontainerregistry.azurecr.io/dsb/messagebroker"` |  |
| image.tag | string | `"canary"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations."kubernetes.io/ingress.class" | string | `"azure/application-gateway"` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"dsb-test.energyweb.org"` |  |
| ingress.hosts[0].paths[0].backend.service.name | string | `"dsb-messagebroker-test"` |  |
| ingress.hosts[0].paths[0].backend.service.port.number | int | `80` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls | list | `[]` |  |
| messagebroker.config.cacheServerUrl | string | `"https://identitycache-staging.energyweb.org/v1"` | (optional string, default https://volta-identitycache.energyweb.org/v1) An URL to Identity Cache server, more info https://github.com/energywebfoundation/iam-cache-server |
| messagebroker.config.mbDid | string | `"did:ethr:0x5aEa5Bf5c5b341A0BF30Cc5b51b77Fb9807F1b52"` | (required string) it is the DID identifier corresponding to the PRIVATE_KEY |
| messagebroker.config.natsClusterUrl | string | `"nats://dsb-nats.dsb.svc:4222"` | NATS Jetstream node url |
| messagebroker.config.port | int | `3000` | (optional int, default 3000) Port number to be used by DSB Message Broker to listen to |
| messagebroker.config.webUrl | string | `"https://volta-rpc.energyweb.org/"` | (optional string, default https://volta-rpc.energyweb.org/) An URL to EW blockchain node (default |
| messagebroker.config.withSwagger | string | `"true"` | (optional bool, default true) Boolean that enables or disables hosting Swagger API documentation alongside DSB Message Broker endpoints, if true then http://{URL}:{PORT}/swagger is available |
| nameOverride | string | `"dsb-messagebroker"` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `80` |  |
| service.type | string | `"LoadBalancer"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
