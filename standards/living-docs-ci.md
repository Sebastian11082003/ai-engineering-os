# Estándar: CI de documentación viva

## Propósito

La documentación viva no puede depender de un checkbox. Si cambia backend, frontend, base de datos o infraestructura, el PR **no se fusiona** hasta que el mismo entregable actualice los documentos mapeados.

Esto aplica la regla 11 de [FRAMEWORK_RULES.md](../FRAMEWORK_RULES.md) y el principio SDD de [documentation-framework.md](../core/modules/documentation-framework.md): si el código cambió y el documento no, el documento está roto.

## Qué verifica el pipeline

El job `Documentación viva` compara el PR contra su rama base y clasifica los archivos:

| Superficie | Ejemplos de código | Docs que deben cambiar en el mismo PR |
|---|---|---|
| backend | `backend/`, `apps/api/`, rutas, controladores, OpenAPI en código | `docs/07-api/`, `docs/09-microservices/`, `docs/05-architecture/` |
| frontend | `frontend/`, `apps/web/`, páginas, componentes | `docs/12-ux-ui/`, `docs/07-api/`, `docs/14-training/` |
| database | `migrations/`, Prisma, Alembic, SQL de esquema | `docs/06-data/`, `docs/09-microservices/` |
| devops | workflows, Docker, Terraform, Helm | `docs/10-devops/`, `docs/13-operations/` |

No basta con tocar un archivo vacío: el diff de documentación tiene que incluir al menos una línea con contenido.

El CI **no** juzga si el texto es correcto. Eso lo revisa el agente responsable y el Orchestrator. El CI solo impide el merge sin evidencia de actualización.

## Cómo se instala en un proyecto consumidor

1. Copiar [templates/ci/living-docs-workflow.yml](../templates/ci/living-docs-workflow.yml) a `.github/workflows/living-docs.yml`.
2. Copiar [templates/ci/living-docs.json](../templates/ci/living-docs.json) a `.living-docs.json` y ajustar globos a la estructura real del repo.
3. Copiar [scripts/check-living-docs.js](../scripts/check-living-docs.js) a `scripts/check-living-docs.js`.
4. En GitHub: **Settings → Branches → Branch protection** (o Rulesets) sobre `main`:
   - Require a pull request before merging
   - Require status checks to pass: **Documentación viva**
   - No permitir bypass del check salvo administradores en emergencia, y registrar la excepción en `docs/15-project-control/`

Sin el paso 4 el workflow corre pero un merge directo sigue siendo posible. La puerta real es el status check obligatorio.

## Excepciones

No hay skip por etiqueta, comentario ni `[skip docs]` cuando cambian backend, frontend o base de datos.

Solo quedan fuera del gate los archivos de [`.living-docs.json`](../.living-docs.json) en `ignore` (lockfiles, binarios, `dist/`). Un cambio de formato que no altera comportamiento debe ir en un PR que no toque esas superficies, o incluir la nota documental de que el contrato no cambió (por ejemplo una línea en el README del servicio: "sin cambio de interfaz").

## Correlaciones

- Reglas de redacción: [documentation-rules.md](documentation-rules.md)
- DoD: [checklists/definition-of-done.md](../checklists/definition-of-done.md)
- Playbook: [playbooks/documentation-stage-playbook.md](../playbooks/documentation-stage-playbook.md)
