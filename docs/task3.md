# Task 3 – Istio Service Mesh Security

## Implemented

- Istio Installation
- Automatic Sidecar Injection
- PeerAuthentication (STRICT mTLS)
- AuthorizationPolicy

## Testing

### Allowed

reporting → ledger-api

Request successfully reached the application.

### Denied

test → ledger-api

Request denied with RBAC authorization.

## Certificate Rotation

Istio automatically issues and rotates workload certificates using istiod.

## Trust Model

All workloads trust the mesh root CA and mutually authenticate using short-lived certificates.