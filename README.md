# Leruchi — VibeDB Core

**A developer-first, agent-native database platform designed to bridge relational and graph workloads.**

Leruchi is building VibeDB Core around a typed query and mutation interface, a secure execution boundary, tenant isolation, and developer tooling for applications and AI agents.

## Project status

VibeDB Core is in active engineering and release-candidate review. This repository is the intended **public home for the approved open-source core**. The reviewed source export has not yet been published here as a versioned release, so this repository should not yet be treated as a stable install target.

Engineering work and CI validation currently happen in [Leruchi-development](https://github.com/Leruchii/Leruchi-development). Only the explicitly reviewed and approved open-source export should be promoted from that repository; internal/control-plane material is not part of the public distribution.

## Design goals

- **Relational + graph:** give developers a coherent interface across SQL-backed and graph-oriented data.
- **Safe by default:** enforce trusted tenant context, validation, capability checks, and a secure execution boundary.
- **Agent-native:** provide APIs and tooling that AI agents and MCP-enabled clients can use with explicit, scoped permissions.
- **Developer-focused:** build SDK, CLI, schema/catalog, diagnostics, and operational visibility into the workflow.
- **Node.js 24:** Node.js 24 is the supported JavaScript runtime baseline; Node.js 20 is not supported.

## Before using this project

- No versioned public release is available from this repository yet.
- Do not use this repository as evidence of production readiness.
- Production identity-provider integration, signing-key operations, production database-role hardening, private networking, monitoring, and recovery validation remain deployment requirements.
- Third-party dependency licensing and attribution review must be resolved before a formal release. See the development repository's `THIRD_PARTY_NOTICES.md` for the current inventory; that inventory is not legal advice or legal clearance.

## Development and release process

1. Build and test in [Leruchi-development](https://github.com/Leruchii/Leruchi-development).
2. Generate the allowlisted source export and verify the exact source commit and artifact digests.
3. Review source boundaries, security scan results, and third-party notices.
4. Promote only the approved export here and publish a versioned release with accurate engineering-preview limitations.

Until a versioned release is published, treat the project as an active engineering effort rather than a stable production dependency.
