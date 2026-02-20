<div align="center">

# No Secrets

<img src="assets/logo.png" alt="No Secrets" width="128" />

[![Cursor Plugin](https://img.shields.io/badge/Cursor-Plugin-blue)](https://cursor.com/marketplace)

</div>

**Cursor plugin** — Detect possible secrets in your code and get clear remediation (env vars, secret managers). Install in Cursor and run `/no-secrets` or ask the agent to scan for secrets. Designed to reduce false positives and work alongside CI and pre-commit tools.

## Install in Cursor

This repo is a [Cursor](https://cursor.com) plugin. To use it:

- **From this repo:** In Cursor, add a plugin from a Git URL: `https://github.com/raksbisht/no-secrets`, or clone the repo and add the plugin from the `no-secrets` folder.
- **From the marketplace:** Install from the [Cursor Marketplace](https://cursor.com/marketplace) when published.

```bash
/add-plugin no-secrets
```

## Components

### Skills

| Skill | Description |
|:------|:------------|
| `no-secrets-scan` | Scan files for secret-like patterns; report findings with type, file, line, and suggested fix; support scope (file / staged / changed). |

### Rules

| Rule | Description |
|:-----|:------------|
| `no-secrets-policy` | Prefer env vars or a secret manager; when the user asks to scan for secrets or run a pre-commit/pre-push check, run the no-secrets scan. |

### Commands

| Command | Description |
|:--------|:------------|
| `no-secrets` | Run the no-secrets scan (default: staged or changed files). |

## Usage

- **Command:** Use `/no-secrets` to run the scan (default scope: staged or changed files).
- **Chat:** Ask to "scan for secrets", "run no-secrets", or "check for leaked keys" to run the same workflow.
- **Before push:** Run `/no-secrets` or ask for a scan before pushing; the plugin reports and suggests fixes—it does not block or rewrite files.

## What we scan for

- API keys (generic patterns, `sk_`, `pk_`, `ghp_`, `xoxb_`, etc.), connection strings, Bearer tokens, private key content, and high-entropy strings in config-like context.
- We skip common placeholders and test/fixture paths when possible; findings are reported with confidence (high/medium/low) where applicable.

## What we don't do

- We do not modify or delete content; we report and suggest remediation.
- We recommend using CI (e.g. secret scanning) for pushed code and keeping `.env` in `.gitignore` with a `.env.example` for documentation.

## Author & support

**Rakesh Bisht** — [GitHub](https://github.com/raksbisht). For bugs or feature requests, open an [issue](https://github.com/raksbisht/no-secrets/issues).

## License

MIT
