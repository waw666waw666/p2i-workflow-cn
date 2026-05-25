# Security Policy

## Scope

This repository is a documentation-first prompt workflow project.

It should not contain:

- private API keys
- access tokens
- production credentials
- copied private prompt libraries

## Reporting

If you notice a security issue or accidental secret exposure:

1. Do not open a public issue with the secret content
2. Remove or rotate the exposed secret first if you control it
3. Contact the repository owner privately before broad disclosure

## Safe contribution guidance

- Never commit `.env` files with real credentials
- Never paste live tokens into examples
- Never include proprietary prompt datasets without permission
- Prefer placeholder values in documentation
