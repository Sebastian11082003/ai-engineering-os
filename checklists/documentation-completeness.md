# Completitud de documentación

El Orchestrator usa este checklist al cerrar la etapa de documentación de un proyecto consumidor. Cada ítem requiere archivo con contenido real o justificación escrita de por qué no aplica. Ver [playbooks/documentation-stage-playbook.md](../playbooks/documentation-stage-playbook.md).

## Fase 1 — Descubrimiento

- [ ] `01-context/overview.md`
- [ ] `01-context/scope.md` (dentro y fuera)
- [ ] `01-context/glossary.md`
- [ ] `02-domain/domain-map.md`
- [ ] `02-domain/entities-and-rules.md`
- [ ] `02-domain/domain-events.md` (o no aplica, justificado)
- [ ] `03-product/problem-framing.md`
- [ ] `03-product/vision.md`
- [ ] Gate de stakeholder cerrado

## Fase 2 — Definición

- [ ] Historias con Gherkin y trazabilidad
- [ ] NFR medibles
- [ ] Matriz de trazabilidad
- [ ] Overview C4 (Contexto y Contenedores)
- [ ] ADRs individuales de las decisiones relevantes
- [ ] Modelo de datos
- [ ] Contratos OpenAPI (o no aplica, justificado)
- [ ] Gate de arquitectura cerrado

## Fase 3 — Diseño detallado

- [ ] Índice de diagramas y al menos un flujo crítico
- [ ] Catálogo de servicios/módulos
- [ ] Ficha de cada servicio/módulo (README + data-model)
- [ ] Mapa de navegación / UX (o no aplica, justificado)
- [ ] Autorización explícita antes de implementar

## Gobernanza y control

- [ ] `00-governance` con DoR y DoD del proyecto
- [ ] Workflow de documentación viva configurado como required check
- [ ] `15-project-control/risks.md`
- [ ] Índice consolidado mantenido por Documentation Engineer
