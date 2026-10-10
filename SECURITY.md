# Security Policy

Leruchi treats tenant isolation, authorization boundaries, and credential handling as security-critical.

## Reporting a vulnerability

Please do not disclose suspected vulnerabilities in a public issue or pull request.

Use GitHub's private vulnerability reporting feature for this repository when available. If private reporting is unavailable, contact the maintainers privately through the Leruchii organization before sharing technical details. Include the affected version or commit, impact, and a minimal reproduction when safe to do so.

Do not include real customer data, production credentials, tokens, private keys, or other secrets in a report.

## Security boundaries

- PostgreSQL row-level security is authoritative for tenant isolation.
- Normal clients and AI agents must not receive unrestricted service-role credentials.
- MCP is an interface, not a privileged execution path.
- Node.js 24 is the supported runtime.
- Passing an automated security profile is not a claim of full compliance with any external standard.

## Historical Compose placeholder findings

The historical Gitleaks findings for `VAULT_ENC_KEY` at the exact fingerprints in `.gitleaksignore` were reviewed against the tracked Compose context. They refer to a fixed Stage 03 local-development placeholder, not an owner-provided production credential. The placeholder has been removed from the current Compose files; startup now requires `VAULT_ENC_KEY` from the local environment or an untracked `.env` file.

The ignore entries are fingerprint-specific and do not disable the Gitleaks rule or suppress new occurrences. Never reuse a development value in staging or production. Production keys must be generated, stored, rotated, and accessed through the approved secret-management mechanism.

The separately exposed GitHub credential is treated as rotated based on the repository owner's confirmation. This owner confirmation is distinct from repository scanning and does not replace the checks for any separate credential exposure.


## Public export historical Gitleaks dispositions

The sanitized public repository history contains three exact historical findings for the same fixed local-development Supavisor `VAULT_ENC_KEY` placeholder already documented in the development repository's security history. The current public tree requires a fresh local-only value through environment interpolation; no static key is retained in current Compose files. The findings are suppressed only by their exact commit-specific fingerprints in `.gitleaksignore`; new values and findings remain blocking. The owner must ensure the historical value was never used in a shared or production environment; if there is any doubt, rotate it in the relevant environment and investigate exposure.
