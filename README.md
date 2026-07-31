# Ledger API Assignment

## Overview

Brief description of the project.

## Architecture

- Kubernetes
- Istio Service Mesh
- GitHub Actions
- Container Security

## Task 1 – Kubernetes Hardening

- Namespace
- RBAC
- ServiceAccount
- ConfigMap
- Secret
- Resource requests/limits
- Liveness & Readiness probes
- SecurityContext
- NetworkPolicy
- Ingress

## Task 2 – Secure CI/CD

- GitHub Actions
- Semgrep
- Gitleaks
- Trivy Filesystem Scan
- Docker Build
- Trivy Image Scan
- Push to GHCR

## Task 3 – Istio Security

### Sidecar Injection

Explain how namespace injection was enabled.

### mTLS

Explain PeerAuthentication STRICT mode.

### AuthorizationPolicy

Explain only the reporting service can call ledger-api.

### Certificate Rotation

Istio automatically provisions and rotates workload certificates using istiod.

### NetworkPolicy vs AuthorizationPolicy

(Table)

## Testing

### Allowed

reporting → ledger-api ✅

### Denied

test pod → ledger-api ❌ (RBAC)

## Screenshots

(Add screenshots)

## Repository Structure

(tree)

## Future Improvements

- Cosign image signing
- SLSA provenance
- GitOps deployment