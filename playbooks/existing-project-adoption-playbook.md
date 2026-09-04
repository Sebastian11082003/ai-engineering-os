# Playbook: Adoptar SDD en un proyecto existente

## Propósito

Aplicar AI Engineering OS a un repositorio que **ya tiene código y documentación**, sin reescribir lo que ya sirve.

El playbook de etapa ([documentation-stage-playbook.md](documentation-stage-playbook.md)) asume un proyecto que se documenta desde cero. Este playbook cubre el otro caso: el producto ya opera. La regla 12 manda: estabilidad primero. Mover carpetas o reescribir ADRs no es el primer incremento.

## Cuándo usarlo

- El repo tiene `docs/` (u otra convención) que no es `00`–`15`.
- Hay backend, frontend o base de datos en uso.
- Reescribir la documentación pondría en riesgo un flujo que ya opera, o gastaría un ciclo sin cambiar comportamiento.

Si el proyecto está vacío, usa el playbook de etapa, no este.

## Qué no hacer en el primer incremento

- No renombrar ni mover documentos existentes.
- No crear las 16 carpetas SDD vacías "para cumplir".
- No copiar el `.living-docs.json` del OS (ese mapa es del framework).
- No copiar `templates/ci/living-docs.json` sin ajustar rutas a **los archivos que ya existen**.
- No introducir un patrón de docs nuevo (p. ej. forzar OpenAPI en disco) si el contrato ya vive en Swagger/código y no hay consumidor que lo pida ahora.

## Secuencia

### 1. Inventario (Orchestrator + Documentation Engineer)

Listar lo que ya existe y clasificarlo. Una tabla basta. No se redacta de nuevo.

Pregunta por cada artefacto SDD de [standards/documentation-structure.md](../standards/documentation-structure.md):

| Estado | Acción |
|---|---|
| Existe, útil, otra ruta | Mapear. No mover. |
| Existe, desactualizado respecto al código | Anotar como deuda en control de proyecto. No reescribir en este incremento salvo que el siguiente cambio de código lo toque. |
| No existe y sí aplica | Crear **un** archivo corto con contenido real, o justificar por qué se difiere (fecha + riesgo). |
| No aplica | Un archivo o una fila en el mapa que diga por qué. La ausencia silenciosa no es proporcionalidad. |

### 2. Mapa SDD (Documentation Engineer)

Crear un único índice en el repo consumidor, por convención `docs/sdd-mapping.md`.

El mapa:

- usa los números `00`–`15` como **índice**, no como carpetas obligatorias todavía;
- apunta a rutas reales (`docs/architecture/c4-context.md`, `.ai-engineering/PROJECT_STATE.md`, …);
- marca huecos con `faltante` o `no aplica` + motivo;
- se actualiza cuando un documento nuevo se crea en la convención SDD.

Los documentos nuevos **sí** nacen en `docs/00-governance`, `docs/15-project-control`, etc. Lo viejo se queda. No se mantienen dos redacciones del mismo hecho.

### 3. Puerta de documentación viva (Backend/Frontend según el stack)

1. Copiar [scripts/check-living-docs.js](../scripts/check-living-docs.js).
2. Copiar [templates/ci/living-docs-workflow.yml](../templates/ci/living-docs-workflow.yml) y añadir la rama de trabajo real (`dev` si `main` no es donde se integra).
3. Escribir `.living-docs.json` **a medida**:
   - `code` = globs del código que existe (`backend/**`, `frontend/**`, `**/prisma/**`, `docker/**`).
   - `docs` = rutas del inventario, no `docs/07-api/**` si esa carpeta no existe.
   - `requireDocsRootChange`: `false` si el estado vive fuera de `docs/` (por ejemplo `.ai-engineering/`).
4. El primer PR que añade el workflow debe actualizar el mapa o el changelog del proyecto. Si no, el propio job se bloquea (superficie devops).
5. Pedir el status check required cuando el job ya pasó una vez en la rama protegida.

Guía: [standards/living-docs-ci.md](../standards/living-docs-ci.md).

### 4. Gate de adopción

El Orchestrator no cierra este playbook sin:

- [ ] Inventario escrito (el mapa).
- [ ] Living-docs en verde contra la rama de integración.
- [ ] Huecos listados con dueño o "no aplica".
- [ ] Ningún archivo histórico movido en este incremento.
- [ ] Autorización explícita antes de cualquier migración de carpetas.

### 5. Migración posterior (solo con autorización)

Cuando un documento existente se toque de verdad (el código cambió y el texto ya no es cierto):

1. Actualizar el archivo **en su ruta actual**, o
2. Crear el artefacto SDD nuevo, mover el viejo a `docs/99-archive/` con fecha y motivo, y corregir el mapa.

No se migra "el árbol completo" en un solo PR. Un artefacto por entregable, cuando el cambio de comportamiento lo obliga.

## Relación con la regla 12

1. **Estabilidad** — el producto sigue operando; las rutas que el equipo ya usa no se rompen.
2. **Clean code / clean docs** — un índice claro vale más que 16 carpetas vacías.
3. **Patrón SDD 00–15** — se aplica a lo nuevo; lo viejo se mapea hasta que un cambio real justifique moverlo.

## Origen

La brecha original (lista de documentos obligatorios → entrega incompleta) se cerró con el playbook de etapa. Este playbook cierra la brecha siguiente: aplicar SDD a un backend o SaaS que ya existe sin fingir que el proyecto empieza en `01-context`.
