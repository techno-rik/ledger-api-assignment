# Ledger API Assignment

## Overview

This repository contains the implementation of a secure DevSecOps workflow for the Ledger API application. The assignment demonstrates Kubernetes deployment hardening, a secure CI/CD pipeline, and service-to-service security using Istio.

---

# Architecture

The solution consists of:

- Kubernetes (Kind Cluster)
- Ledger API Deployment (3 replicas)
- Reporting Service
- Kubernetes Service (ClusterIP)
- Istio Service Mesh
- GitHub Actions CI/CD
- GitHub Container Registry (GHCR)

---

# Task 1 – Kubernetes Hardening

The application was deployed following Kubernetes security best practices.

### Implemented

- Dedicated Namespace
- ConfigMap
- Secret
- ServiceAccount
- Role & RoleBinding (RBAC)
- Deployment with 3 replicas
- ClusterIP Service
- Ingress
- NetworkPolicy
- Resource Requests & Limits
- Liveness Probe
- Readiness Probe
- SecurityContext

**Result**

The application was successfully deployed to the Kind cluster with all required hardening controls enabled.

---

# Task 2 – Secure CI/CD Pipeline

A GitHub Actions pipeline was implemented to automate build and security validation.

## Pipeline Steps

1. Checkout Repository
2. Setup Python
3. Semgrep Static Analysis
4. Gitleaks Secret Scan
5. Trivy Filesystem Scan
6. Docker Image Build
7. Trivy Image Scan
8. Push Image to GitHub Container Registry (GHCR)

## Security Tools

- Semgrep (SAST)
- Gitleaks (Secret Detection)
- Trivy (Filesystem & Container Vulnerability Scanning)

---

# Task 3 – Istio Service Mesh Security

## Sidecar Injection

Automatic sidecar injection was enabled for the `payments` namespace, allowing Envoy proxies to be injected into each workload.

## mTLS

STRICT PeerAuthentication was configured to ensure encrypted and authenticated service-to-service communication inside the service mesh.

## AuthorizationPolicy

An Istio AuthorizationPolicy was created to allow only workloads using the **reporting** ServiceAccount to access the Ledger API.

## Certificate Rotation

Istio automatically provisions short-lived X.509 certificates through `istiod`. Certificates are rotated automatically before expiration, and all workloads trust the mesh root CA for mutual authentication.

## NetworkPolicy vs AuthorizationPolicy

| NetworkPolicy | AuthorizationPolicy |
|---------------|---------------------|
| Controls Layer 3/4 network traffic | Controls Layer 7 service authorization |
| Based on IPs and ports | Based on workload identity and HTTP attributes |
| Enforced by Kubernetes CNI | Enforced by Istio Envoy sidecars |
| Restricts network connectivity | Restricts application-level access |

---

# Testing

## Authorized Communication

The Reporting service successfully communicated with the Ledger API through the Kubernetes Service, confirming successful service discovery and Istio mTLS.

**Result:** Allowed

---

## Unauthorized Communication

A temporary test pod attempted to access the Ledger API and was denied by the Istio AuthorizationPolicy.

**Result:** RBAC Access Denied

---

# Screenshots

The repository includes screenshots demonstrating:

- Kubernetes deployment
- GitHub Actions workflow
- Semgrep scan
- Trivy scans
- Istio PeerAuthentication
- AuthorizationPolicy
- Authorized service communication
- Unauthorized access blocked by RBAC

Screenshots are available in the `screenshots/` directory.

---

# Repository Structure

```
app/
deploy/
docs/
reports/
screenshots/
.github/workflows/
README.md
```

---

# Future Improvements

- Container image signing using Cosign
- SLSA build provenance
- GitOps deployment with Argo CD
- Continuous policy enforcement with Kyverno
- Runtime threat detection using Falco