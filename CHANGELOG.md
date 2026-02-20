# Changelog

## 1.0.0

- Initial release.
- Skill: `no-secrets-scan` — detect secret-like patterns, report with remediation, scope (file / staged / changed), confidence where applicable.
- Rule: `no-secrets-policy` — prefer env/secret manager; run scan when user asks for secret check or pre-commit/pre-push check.
- Command: `no-secrets` — run the no-secrets scan.
