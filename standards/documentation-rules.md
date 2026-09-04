# Estándar de Reglas de Documentación

## Propósito

Definir cómo se escribe, actualiza y rechaza documentación en cualquier proyecto consumidor de este OS. Un documento que no sigue estas reglas puede rechazarse en revisión, igual que código que no pasa lint.

## Principio central

> La documentación es código. Si no está al día, está rota.

Toda historia que cambia el comportamiento del sistema incluye la actualización de los documentos afectados en el mismo entregable. El [Definition of Done](../checklists/definition-of-done.md) lo exige.

## Idioma

El OS (este repositorio) se escribe en **español**.

En un proyecto consumidor el idioma se fija en `00-governance` mediante ADR. Una vez elegido, es vinculante por categoría (código, commits, markdown, contratos). Mezclar idiomas en la misma categoría es motivo de rechazo.

Recomendación por defecto del OS: markdown y comunicación de producto en el idioma del stakeholder; identificadores de código, ramas y commits en inglés (Conventional Commits).

## Convenciones de archivos

- Contenido: `kebab-case.md`
- Plantillas: prefijo `_` (`_template-adr.md`, `_template-hu.md`)
- ADRs: `ADR-NNN-titulo-corto.md`, numeración secuencial
- Contratos OpenAPI: `nombre-del-servicio.yaml`
- Cada sección tiene un `README.md` que explica su propósito **antes** de llenar los documentos

## Qué documentar y qué no

### Sí documentar

| Qué | Dónde |
|---|---|
| Decisiones de arquitectura no obvias | `05-architecture/decisions/records/` |
| Reglas de negocio e invariantes | `02-domain/entities-and-rules.md` |
| Contratos de API | `07-api/contracts/openapi/` |
| Cambios de modelo de datos | `06-data/models.md` y ficha del servicio |
| Procedimientos operativos | `13-operations/` y runbooks |
| Riesgos, bloqueos y deuda | `15-project-control/` |

### No documentar

- Lo que el código ya dice con claridad
- Experimentos temporales que se van a revertir
- Detalle interno de librerías de terceros
- Historial de cambios (eso es `git log`); el changelog del producto sí se mantiene

## Formato

- Un solo `#` por archivo (título).
- `##` secciones, `###` subsecciones. Si se necesita H4, el documento tiene demasiada jerarquía: partirlo.
- Tablas para registros, matrices y comparaciones. No para listas simples.
- Bloques de código con lenguaje indicado.
- Bloques `> [!NOTE] INSTRUCCIONES` marcan plantilla sin llenar. Se eliminan cuando el documento está completo.

## Pregunta previa a crear un documento

Antes de crear un archivo nuevo: ¿quién lo lee, cuándo, y qué decisión permite tomar? Si no hay respuesta a las tres, no se crea todavía ([documentation-framework.md](../core/modules/documentation-framework.md)).

## Proceso de actualización

1. Quien abre el cambio identifica los documentos afectados (tabla de dependencias cruzadas en [documentation-structure.md](documentation-structure.md)).
2. Actualiza documentos y código en el mismo entregable.
3. El revisor verifica que la documentación coincida con el comportamiento.
4. Si hay impacto de API, el contrato OpenAPI se actualiza **en el mismo cambio**.
5. El pipeline de [living-docs-ci.md](living-docs-ci.md) bloquea el PR si el código de una superficie cambió y los docs mapeados no. Un checkbox en la plantilla de PR no sustituye ese job.

## Propietarios

El mapeo de agentes por carpeta está en [documentation-structure.md](documentation-structure.md). En el proyecto consumidor, `00-governance` puede nombrar personas concretas; no puede contradecir ese mapeo sin ADR.

## Correlaciones

- Estructura: [documentation-structure.md](documentation-structure.md)
- DoD: [checklists/definition-of-done.md](../checklists/definition-of-done.md)
- DoR: [checklists/definition-of-ready.md](../checklists/definition-of-ready.md)
- Plantillas: [templates/docs](../templates/docs)
- CI de documentación viva: [living-docs-ci.md](living-docs-ci.md)
