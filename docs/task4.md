# Additional Security Controls

## NetworkPolicy

Restricts pod-to-pod communication at Layer 3/4.

## AuthorizationPolicy

Restricts service access using workload identity (ServiceAccount).

## Difference

NetworkPolicy controls network connectivity.

AuthorizationPolicy controls workload authorization and application-layer access.

## Future Improvements

- Cosign image signing
- SLSA provenance
- OPA Gatekeeper
- GitOps deployment