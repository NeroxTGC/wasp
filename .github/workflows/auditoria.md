---
description: |
  Audit of existing docs and blog pages against the code and docs of this same version.
  Custom flow for the gh-aw gap test (part B). Reports an issue, changes nothing.

on:
  push:
    branches: [auditoria-completa]
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

Páginas indicadas: todas las páginas de `web/docs` y todos los posts de `web/blog`.

No menciones a personas, issues, pull requests ni otros repositorios: nada de `@nombres`, `#123`, `owner/repo#123` ni enlaces a github.com.
