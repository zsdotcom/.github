# How to apply this update to `github.com/zsdotcom/.github`

This bundle extends what's already in your project's `.github-template/` — nothing here
contradicts `00`–`05`; it adds a researched, always-free automation/agentic layer on top.
Read `reference-docs/06-AGENTIC-AUTOMATION-STACK.md` first — it explains what each tool does,
what it costs, and the recommended order to turn things on.

## 1. What goes into the `.github` repo itself (auto-inherits org-wide)

Upload everything in `.github-repo-v2/` **except** `workflows-to-copy-per-repo/` into the root
of `github.com/zsdotcom/.github`, preserving structure:

```
zsdotcom/.github/
├── profile/README.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── SUPPORT.md
├── FUNDING.yml
├── labels.yml
├── PULL_REQUEST_TEMPLATE.md
├── MCP-SETUP.md                 # new — maintainer-facing, informational only
├── CODEOWNERS.template          # new — rename + copy per repo, see file header
├── ISSUE_TEMPLATE/
│   ├── config.yml
│   ├── bug_report.yml
│   └── feature_request.yml
├── DISCUSSION_TEMPLATE/
│   └── governance.yml           # new — only takes effect where Discussions is enabled
└── workflows/
    └── stale.yml
```

Only `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `SUPPORT.md`, `FUNDING.yml`,
`ISSUE_TEMPLATE/`, `PULL_REQUEST_TEMPLATE.md`, and `profile/README.md` actually auto-propagate
per GitHub's rules. `MCP-SETUP.md`, `CODEOWNERS.template`, `DISCUSSION_TEMPLATE/`, `labels.yml`,
and everything in `workflows/` are reference material other repos/workflows pull from — they
don't magically apply themselves, same as your original bundle already documented.

## 2. What goes into individual repos, one at a time (never auto-inherited)

Everything in `.github-repo-v2/workflows-to-copy-per-repo/` is a standalone workflow file.
Copy the ones relevant to a given repo into that repo's own `.github/workflows/`. Follow the
build order in `06-AGENTIC-AUTOMATION-STACK.md` §3 rather than adding all of them to every repo
on day one — most have no value until the repo has real content/contributors.

Two files are not workflows and need a rename/placement step:
- `CODEOWNERS.template` → copy into a repo, rename to `CODEOWNERS`, edit the team names.
- `claude-pr-assistant.yml` → **optional and paid** (needs your own `ANTHROPIC_API_KEY`
  secret). Skip it entirely if you want to stay strictly zero-cost.

## 3. Verify

1. Any other `zsdotcom` repo without its own `CONTRIBUTING.md` → **New issue** should show the
   org-wide templates.
2. A repo with `codeql.yml` and `scorecard.yml` copied in → check the **Security** tab after
   the first workflow run for code scanning alerts and the Scorecard result.
3. A repo with `semantic-pr.yml` + `release-please.yml` → open a PR titled without a `feat:`/
   `fix:`/etc. prefix and confirm the check fails as expected.
