# Task 2 – Secure CI/CD Pipeline

## Security Gates

| Stage | Tool | Policy |
|--------|------|--------|
| SAST | Semgrep | Fail on HIGH findings |
| Secret Scan | Gitleaks | Fail if secrets detected |
| Dependency Scan | Trivy FS | Fail on HIGH/CRITICAL CVEs |
| Image Scan | Trivy Image | Fail on HIGH/CRITICAL CVEs |
| Image Signing | Cosign | Fail if signing fails |

## CVE Policy

If a CVE has no available fix:

- Document the risk.
- Apply compensating controls.
- Monitor vendor advisories.
- Upgrade once a fix is available.

## GitOps

ArgoCD is configured with automated sync, pruning, and self-healing to ensure the cluster state always matches Git.