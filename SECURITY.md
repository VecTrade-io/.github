# Security Policy

## Reporting a Vulnerability

The VecTrade team takes security vulnerabilities seriously. We appreciate your efforts to responsibly disclose your findings.

**DO NOT** file a public GitHub issue for security vulnerabilities.

### How to Report

1. **Email**: Send details to `security@vectrade.io`
2. **Encrypt** (optional): Use our PGP key (available at `https://vectrade.io/.well-known/security.txt`)
3. **Include**:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if any)

### Response Timeline

| Action | Timeline |
|--------|----------|
| Acknowledgment | Within 24 hours |
| Initial assessment | Within 72 hours |
| Fix development | Within 7 days (critical) / 30 days (non-critical) |
| Public disclosure | After fix is released + 30 days |

### Scope

The following are in scope for security reports:

- VecTrade API endpoints (`api.vectrade.io`)
- Official SDKs (`vectrade-python`, `@vectrade/sdk`)
- CLI (`vectrade-cli`)
- Authentication and authorization mechanisms
- Data exposure vulnerabilities
- Dependency vulnerabilities in official packages

### Out of Scope

- Denial of service (DoS) attacks
- Social engineering
- Physical security
- Third-party services (Stripe, Cloudflare, etc.)
- Community-maintained SDKs

## Supported Versions

| Version | Supported |
|---------|-----------|
| Latest major | ✅ Full support |
| Previous major | ✅ Security fixes only (12 months) |
| Older | ❌ Not supported |

## Security Practices

### API Keys

- Keys are stored as SHA-256 hashes only (raw key never persisted)
- Key prefix `vq_` enables identification without exposure
- Keys can be revoked immediately via API or dashboard
- Per-key rate limits and quota enforcement

### Supply Chain

- All releases signed with provenance attestation (SLSA Level 2)
- Dependencies audited weekly (Renovate + npm audit + pip-audit)
- Ephemeral CI runners with pinned action versions
- SBOM generated for every release

### Data Protection

- TLS 1.3 enforced for all API traffic
- PII encrypted at rest (AES-256)
- No raw API keys stored — SHA-256 hash only
- Payment data never stored (delegated to Stripe)
- 90-day log retention policy

## Bug Bounty

We plan to launch a formal bug bounty program via HackerOne. Until then, valid security reports will be acknowledged in our security advisories and contributors may receive VecTrade Professional credits.

## Security Advisories

Security advisories are published on the affected repository's Security tab (e.g., `https://github.com/VecTrade-io/vectrade-python/security/advisories`).

Subscribe to notifications via GitHub's Watch → Security alerts on any repo you depend on.
