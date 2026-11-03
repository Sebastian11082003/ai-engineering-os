# CI y publicación

## En cada pull request

El workflow `CI` del repositorio:

- corre la documentación viva del OS;
- corre la documentación viva de esta app con `LIVING_DOCS_CONFIG=apps/inventario-codigos/.living-docs.json`;
- en el job **Inventario códigos** ejecuta `npm ci`, `npm test` y `npm run build`.

## Publicación

Workflow manual **Inventario en GitHub Pages** (`workflow_dispatch`). Construye con la base del nombre del repo, sube `dist/` y lo publica con las acciones oficiales de Pages.

Cloudflare Pages, si se usa, construye con `npm ci && npm run build` y publica `dist/`. Los clics están en el README del producto.

No hay secreto que inyectar. No hay migración que correr.
