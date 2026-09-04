# Plantillas de CI

- [living-docs-workflow.yml](living-docs-workflow.yml) → `.github/workflows/living-docs.yml` en el proyecto consumidor.
- [living-docs.json](living-docs.json) → `.living-docs.json` en la raíz del proyecto consumidor (ajustar globos). No copiar el `.living-docs.json` de este OS: ese archivo es el mapa del framework, no el de un producto.
- El script se copia desde [scripts/check-living-docs.js](../../scripts/check-living-docs.js).

Instalación y branch protection: [standards/living-docs-ci.md](../../standards/living-docs-ci.md).
