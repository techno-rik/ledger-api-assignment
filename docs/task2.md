## Security Gate Policy

| Gate | Policy |
|------|--------|
| Semgrep | Block on HIGH findings |
| Gitleaks | Block on any detected secrets |
| Trivy Filesystem | Block on HIGH/CRITICAL application dependency vulnerabilities |
| Trivy Image | Report HIGH/CRITICAL vulnerabilities; do not block if they originate from the base image and no upstream fix is available. These are tracked until a patched base image is released. |

## Handling CVEs Without a Fix

If a vulnerability exists only in the upstream base image and no patched image is available:

- Record the finding.
- Monitor upstream releases.
- Rebuild using the patched base image once available.
- Apply compensating controls such as non-root execution, minimal image, read-only filesystem, and network restrictions.