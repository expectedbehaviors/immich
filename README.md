# Immich Helm Chart

Baseline Helm chart for [Immich](https://immich.app/) (self-hosted photo and video backup). Wraps the [official Immich chart](https://github.com/immich-app/immich-charts) with optional External Secrets for database credentials.

## Subcharts

| Subchart | Source | Values prefix | Description |
|----------|--------|---------------|-------------|
| **immich** | [immich-charts](https://github.com/immich-app/immich-charts) | `immich.*` | Server, ML, Valkey, ingress, persistence. |
| **onepassworditem** | [OnePasswordItem-helm](https://github.com/expectedbehaviors/OnePasswordItem-helm) | `onepassworditem.*` | Optional; disabled by default when using External Secrets. |

## Templates

- **externalsecrets.yaml** — creates `immich-db-credentials` from your ClusterSecretStore when `externalSecrets.dbCredentials.enabled` is true.

## Configuration

Override: `DB_HOSTNAME`, `DB_DATABASE_NAME`, library persistence (`existingClaim` / `subPath`), ingress host, and External Secrets item refs.

## Install

```bash
helm dependency update .
helm template release . -f values.yaml
```
