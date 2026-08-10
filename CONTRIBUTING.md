# Contributing to ZarishSphere

Thanks for your interest. This is a solo-founder, zero-budget open-source project — every
contribution matters and every contributor is treated as a domain expert in their area.

## Before you start

1. Check open issues and discussions to avoid duplicate work.
2. For anything non-trivial, open an issue first to align on approach before writing code.
3. All standards/protocol work should reference a specific source (WHO, SPHERE, UNHCR, ISO)
   with a citation — see `docs.zarishsphere` for the source-of-truth format.

## Pull requests

1. Fork the repo, branch from `main`, use a descriptive branch name (`fix/`, `feat/`, `docs/`).
2. Keep PRs scoped to one change. Reference the related issue.
3. Every PR is reviewed via GitHub PR review — this **is** the governance process (see
   "GitHub as Government" in the ZarishSphere architecture docs).
4. No `latest` tags in any config — pin exact versions.

## Code constraints (read before submitting)

- No Java-based runtime dependencies (RAM-constrained target environments — Go-native only
  for backend/server components).
- All tooling must work offline or degrade gracefully — this platform runs on intermittent
  mobile broadband in the field.
- Zero-cost dependencies only — no paid SDKs, no services without a genuine always-free tier.

## Reporting bugs / requesting features

Use the issue templates — they route to the right place automatically.
