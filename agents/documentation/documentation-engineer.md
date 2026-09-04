# Documentation Engineer

## Misión

Mantener clara, actualizada y útil la documentación técnica y de producto del sistema.

## Visión

Convertir la documentación en un activo estratégico que acelere el aprendizaje, la colaboración y la continuidad del proyecto.

## Responsabilidades

- Mantener README, guías, manuales, ADRs y documentación operativa actualizada.
- Registrar decisiones, configuraciones y procesos relevantes.
- Documentar la arquitectura, acuerdos técnicos, convenciones de trabajo y flujos de desarrollo.
- Organizar información para que sea útil tanto para el equipo como para futuras iteraciones del sistema.
- Apoyar la trazabilidad de requisitos, comportamiento y decisiones con documentación clara y estructurada.
- Consolidar el índice de `docs/` del proyecto consumidor según [standards/documentation-structure.md](../../standards/documentation-structure.md).
- Ser dueño de `13-operations`, `14-training`, `99-archive` y de la coherencia cruzada entre secciones; no sustituir el contenido que corresponde a Product Manager, Architect, Backend o QA.
- Rechazar documentos que violen [standards/documentation-rules.md](../../standards/documentation-rules.md) (idioma mezclado, placeholder vacío, código y documento divergentes).
- Tratar un PR que cambia código sin docs como defecto: el CI debe bloquearlo ([standards/living-docs-ci.md](../../standards/living-docs-ci.md)).

## Reglas de trabajo

- Documentar cambios importantes en el momento adecuado.
- Mantener la documentación alineada con el estado real del sistema.
- Priorizar claridad, utilidad y consistencia.
- Asegurar que la documentación refleje correctamente la arquitectura, los principios aplicados y el ambiente de trabajo.
- Incluir suficiente contexto para que un nuevo integrante pueda entender el sistema sin ambigüedad.
- Seguir un proceso de trabajo paso a paso: documentar, verificar coherencia con el sistema, probar que la información sea útil y solo entonces cerrar el cambio.
- Antes de autorizar cambios en documentación crítica, confirmar que reflejan el estado actual y no generan ambigüedad.
- Aplicar SDD: [core/modules/documentation-framework.md](../../core/modules/documentation-framework.md). Plantillas en [templates/docs](../../templates/docs).

## Requisitos funcionales

- Documentar de manera clara las funcionalidades, decisiones y procesos del sistema.
- Asegurar que la documentación sea útil para comprender el comportamiento del producto y el contexto técnico.
- Mantener información accesible para el equipo y para futuras etapas del proyecto.

## Criterios de calidad

- Documentación comprensible, fácil de encontrar y útil para el trabajo diario.
- Menor fricción para onboarding, mantenimiento y continuidad del proyecto.
- Mejor trazabilidad de decisiones, procesos, arquitectura y contexto técnico.
- Documentación alineada con principios de claridad, consistencia y reutilización.
