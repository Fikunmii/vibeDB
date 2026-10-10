# Leruchi — Engineering Preview

Leruchi is a developer- and AI-agent-oriented data platform that brings relational SQL, graph operations, vector retrieval, realtime changes, and agent workflows behind shared validation and authorization boundaries. Its goal is to bridge SQL-style data access and graph traversal without making clients or agents construct privileged database queries.

**Runtime: Node.js 24 only.** Node.js 20 is not supported.

## Core capabilities

- **PostgreSQL foundation:** relational persistence, migration discipline, tenant isolation, and row-level security.
- **Query and Mutation IRs:** engine-neutral, schema-validated contracts for expressing data-operation intent.
- **Graph and SQL execution:** controlled planning and compiler paths, including PostgreSQL recursive queries and Apache AGE integration.
- **Schema Catalog and Graph API:** metadata and graph operations behind server-side validation and authorization.
- **SDK, CLI, and MCP:** developer and AI-agent interfaces that delegate to shared execution boundaries.
- **Retrieval and explainability:** hybrid retrieval planning, bounded explanations, evaluation, and deterministic artifact hashes.
- **Observability and recovery:** audit events, request correlation, traces, and backup/restore tooling.
- **Studio:** a web interface and browser-level tests for developer workflows.

The Query IR contract is one subsystem of Leruchi; it is not the complete product description. The IR expresses intent only. Schema validation, tenant authorization, cost/depth/result guardrails, planning, and engine compilation must occur behind this boundary.

## Repository layout

- `packages/` — platform contracts, execution, agent, retrieval, and governance modules.
- `apps/studio/` — Studio application and browser tests.
- `infra/` — database migrations, PostgreSQL initialization, and Supabase compatibility configuration.
- `tests/` — regression and integration-oriented tests.
- `scripts/` — operational and release-support tooling.
- `OSS_EXPORT_MANIFEST.json` — explicit allowlist for the sanitized public source export.

The development and CI repository is [Leruchii/Leruchi-development](https://github.com/Leruchii/Leruchi-development). It holds the engineering plan, internal build-state records, CI definitions, and candidate-generation controls. This repository is the public-facing source destination; the development repository must not be mirrored wholesale into it.

## Engineering-preview status

This is an engineering preview, not a declaration of production readiness or full security compliance. The project owner has confirmed approval of the Leruchi product name and legal/release review. Interfaces and schemas may evolve. Automated tests and the OWASP ASVS verification profile are engineering evidence, not a claim of full compliance with ASVS or any other standard.

Before treating production authorization as deployed, the platform still requires verification of production identity-provider integration, authoritative tenant policy, signing-key custody and rotation, least-privilege deployment roles, private networking or mTLS where required, monitoring and alerting, and staging recovery evidence. These production limitations must be closed and verified in the target environment before relying on Leruchi for production workloads.

## Local development

1. Install Node.js 24 and Docker Compose.
2. Review `docker-compose.yml` and `infra/supabase/docker-compose.yml` before starting services.
3. Supply a fresh local-only `VAULT_ENC_KEY` through your shell environment or an untracked `.env` file. The Compose configuration intentionally fails if this value is missing. Never reuse local values in shared, staging, or production environments.
4. Install the root package dependencies with `npm ci --ignore-scripts --no-audit --no-fund`.
5. Start only the services you need, then run the focused test files for the package or stage being changed. The development repository's CI workflows define the authoritative stage-specific validation commands.

The supplied Compose files are for local development and integration testing. Do not expose the configuration to an untrusted network.

## Runtime, dependencies, and licensing

The root package and lockfile target Node.js `>=24 <25`. Use Node.js 24 consistently across development and CI.

`THIRD_PARTY_NOTICES.md` inventories license metadata declared by the root and Studio npm lockfiles. The inventory is not legal advice or a claim that every license is compatible with every distribution model. The exact release artifact, upstream license texts, attribution requirements, and LGPL/MPL/CC-BY components require the applicable review before broader redistribution.

## Security and support

See [SECURITY.md](SECURITY.md) for vulnerability-reporting guidance and the handling of historical local-development placeholder findings. Never commit real credentials, tenant data, signing keys, or production configuration. MCP and the SDK are interfaces, not privileged execution paths; tenant isolation and server-side authorization must remain authoritative.

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution expectations and [LICENSE](LICENSE) for the repository's declared license.
