---
description: |
  Audit of existing docs and blog pages against the code and docs of this same version.
  Custom flow for the gh-aw gap test (part B). Reports an issue, changes nothing.

on:
  push:
    branches: [auditoria-muestra]
    paths: [".auditoria/**"]
  stop-after: "+7d"

engine:
  id: claude
  model: claude-sonnet-5-5

checkout:
  fetch-depth: 1

max-ai-credits: 300
max-daily-ai-credits: 1200

permissions: read-all

network: defaults

timeout-minutes: 45

safe-outputs:
  allowed-github-references: []
  mentions: false
  threat-detection:
    max-ai-credits: 30
  create-issue:
    title-prefix: "[auditoria] "
    labels: [automation, documentation]
    max: 1

tools:
  github:
    toolsets: [all]
  bash: true
---

# Auditoría de páginas

Revisa las páginas indicadas contra el código y la documentación de esta misma versión. Lista las frases que no son ciertas, con el archivo, la línea y la prueba en el código o en la documentación. No cambies nada, abre un issue con la lista.

Páginas indicadas:

- `web/docs/advanced/cli.md`
- `web/docs/deployment/methods/wasp-deploy/railway.md`
- `web/docs/features/auth/overview.md`
- `web/blog/2025-05-28-how-to-run-cron-jobs-in-postgress-without-extra-infrastructure.mdx`
- `web/blog/2026-05-25-wasp-static-prerendering.mdx`
- `web/blog/2022-01-27-waspleau.mdx`
- `web/blog/2022-12-08-fast-fullstack-chatgpt.mdx`
- `web/blog/2023-03-08-building-a-full-stack-app-supabase-vs-wasp.mdx`
- `web/blog/2024-08-20-django-vs-wasp.mdx`
- `web/blog/2024-09-17-from-idea-to-20k-in-days-how-wasp-accelerated-nuloapps-launch.mdx`
- `web/blog/2025-07-07-wasp-launch-week-10.mdx`
- `web/blog/2025-07-14-public-wasp-dev-roadmap.mdx`
- `web/blog/2025-07-15-railway-deployment.mdx`
- `web/blog/2026-03-25-gentle-intro-npm-workspaces.mdx`
- `web/blog/2026-04-23-14k-stars-open-saas-ai-era.mdx`
- `web/blog/2026-04-29-introducing-open-vibe.mdx`
- `web/blog/2026-08-03-wasp-resend-email-provider.mdx`
- `web/docs/advanced/client-customization/customizing-app.md`
- `web/docs/deployment/database.md`
- `web/docs/tutorial/04-entities.md`

No menciones a personas, issues, pull requests ni otros repositorios: nada de `@nombres`, `#123`, `owner/repo#123` ni enlaces a github.com.
