# Penetration Test Report

## Scope

Assessment of the deployed Ledger API infrastructure.

## Security Controls Tested

- Kubernetes RBAC
- NetworkPolicy
- Istio AuthorizationPolicy
- STRICT mTLS

## Findings

### Authorized Workload

reporting ServiceAccount successfully accessed the Ledger API.

Result:
PASS

### Unauthorized Workload

Temporary test pod was denied access.

Result:
PASS (RBAC Denied)

### CI/CD

- Semgrep executed
- Gitleaks executed
- Trivy filesystem scan executed
- Trivy image scan executed

## Conclusion

The deployment demonstrates Kubernetes hardening, secure CI/CD practices, and zero-trust service-to-service communication using Istio.