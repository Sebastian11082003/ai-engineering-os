# Definition of Done (DoD)

Una historia está **Done** cuando cumple **todos** los criterios. Si falta uno, no está Done: vuelve a In Progress. Cerrar sin esto viola las reglas 3 y 10 de `FRAMEWORK_RULES.md`.

## Checklist obligatorio

### Código (cuando la historia incluye implementación)

- [ ] Implementa todos los criterios de aceptación.
- [ ] Revisado y aprobado.
- [ ] Cumple estándares del proyecto (lint/format/CI en verde).
- [ ] No introduce deuda sin registrarla en `15-project-control`.

### Pruebas

- [ ] Hay pruebas de la lógica de negocio nueva, proporcionales al riesgo.
- [ ] Las pruebas relevantes pasan.
- [ ] Los criterios de aceptación están verificados (manual o automático).

### Integración

- [ ] El cambio no rompe otros módulos o servicios.
- [ ] Si cambió la API: contrato OpenAPI actualizado en `07-api/contracts/`.
- [ ] Si cambió el modelo: `data-model.md` del servicio y `06-data/models.md` actualizados.
- [ ] Si hay eventos nuevos o modificados: catálogo de eventos actualizado.

### Documentación

- [ ] README del servicio/módulo actualizado si cambió la interfaz pública.
- [ ] Si hubo una decisión técnica no obvia: ADR creado o actualizado.
- [ ] Los documentos afectados se actualizaron en el mismo entregable ([documentation-rules.md](../standards/documentation-rules.md)).
- [ ] El job **Documentación viva** del CI está en verde ([living-docs-ci.md](../standards/living-docs-ci.md)).

### Despliegue (cuando el incremento se entrega a un entorno)

- [ ] El cambio es integrable a la rama de integración.
- [ ] CI en verde.
- [ ] Smoke básico del entorno destino, si existe.

## Excepciones

Solo con acuerdo explícito del Orchestrator y registro en `15-project-control`:

- Pruebas E2E omitidas por límite de entorno (documentar el riesgo).
- Documentación diferida por urgencia (ticket de deuda con fecha).

## Qué no es Done

- "Funciona en mi máquina" — debe estar en el repositorio y, si aplica, en el entorno acordado.
- "El stakeholder lo vio bien" — eso es aceptación de producto, no DoD de ingeniería.
- Un placeholder vacío en `docs/` — no es evidencia.
- Un PR de backend, frontend o base de datos con el checkbox de docs marcado y el job de documentación viva en rojo.
