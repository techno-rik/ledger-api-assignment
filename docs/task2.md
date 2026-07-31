# Task 2 – Secure CI/CD Pipeline

## Objective

Create a GitHub Actions pipeline with integrated security scanning.

## Pipeline

1. Checkout Source
2. Setup Python
3. Semgrep (SAST)
4. Gitleaks (Secret Scan)
5. Trivy Filesystem Scan
6. Docker Build
7. Trivy Image Scan
8. Push Image to GHCR

## Security Tools

- Semgrep
- Gitleaks
- Trivy

## Result

The CI pipeline automates application security checks before publishing container images.