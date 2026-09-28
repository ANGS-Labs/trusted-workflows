# ANGS Trusted Workflows

Operator-owned reusable GitHub Actions workflows for ANGS trusted delivery.

## Security status

This repository is a trust boundary and is not yet operational. Workflow changes must be reviewed independently from candidate repositories and pinned by full commit SHA when called.

Do not store webhook secrets, GitHub App private keys, OIDC tokens, TLS keys, or attestation signing keys in this repository.

The initial workflow is developed through a draft pull request. It must not be merged or called until all of the following are approved:

- the trusted runner HTTPS URL and OIDC audience;
- policy, evidence profile, and toolchain documents and their SHA-256 digests;
- the fixed candidate verification command;
- immutable third-party Action commit SHAs;
- repository access and CODEOWNERS protection.

The source platform and deployment runbook live in [`ANGS-Labs/angs-platform`](https://github.com/ANGS-Labs/angs-platform).

Operator-owned inputs live under `policy/`, `profiles/`, and `toolchains/`. Recalculate their exact-file digests with:

```sh
shasum -a 256 policy/*.json profiles/*.json toolchains/*.json
```

Any change to one of those documents requires updating the matching workflow and trusted-runner configuration digest before a new immutable workflow commit is approved.
