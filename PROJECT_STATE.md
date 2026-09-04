# PROJECT_STATE

## Estado actual del proyecto

El repositorio se encuentra en una etapa de consolidación como sistema operativo de ingeniería asistida por IA.

## Componentes ya presentes

- Visión y propósito general del framework en [README.md](README.md)
- Guía operativa central en [core/AGENTS.md](core/AGENTS.md)
- Módulos conceptuales y framework de trabajo en [core/modules](core/modules)
- Rol de coordinación en [agents/management/orchestrator.md](agents/management/orchestrator.md)
- Estructura de agentes y equipos por especialidad
- Documentación SDD integrada: estructura 00–15, reglas, playbook, checklists DoR/DoD y plantillas en [templates/docs](templates/docs)
- Puerta de CI de documentación viva: [standards/living-docs-ci.md](standards/living-docs-ci.md), script [scripts/check-living-docs.js](scripts/check-living-docs.js) y job **Documentación viva** en `.github/workflows/ci.yml`

## Estado operativo

- La base conceptual del sistema está definida.
- La arquitectura modular del repositorio está implementada.
- El modelo de coordinación mediante Orchestrator ya está documentado.
- El sistema está listo para usarse como base de trabajo en nuevos proyectos.
- El framework fue puesto a prueba en un proyecto real (una landing page de servicios de software). La prueba evidenció una brecha entre el principio y la práctica: el Orchestrator, al aplicar solo una lista de documentos obligatorios, entregó documentación incompleta. Esa brecha se cerró primero con una estructura corta 00–06.
- La estructura corta se sustituyó por el enfoque SDD del *Microservices Governance Framework* (CORHUILA), adaptado a este OS: [core/modules/documentation-framework.md](core/modules/documentation-framework.md), [standards/documentation-structure.md](standards/documentation-structure.md), [standards/documentation-rules.md](standards/documentation-rules.md), [playbooks/documentation-stage-playbook.md](playbooks/documentation-stage-playbook.md). La proporcionalidad se conserva: no todos los proyectos son microservicios; ningún artefacto se omite en silencio.

## Próximos pasos recomendados

- Validar el playbook SDD en un segundo proyecto real (backend, integración de IA o sistema distribuido), no solo en una landing.
- Revisar si otros módulos conceptuales presentan la misma brecha entre principio y práctica.
- Definir un flujo operativo más detallado para el Orchestrator fuera de documentación (calidad, seguridad).
- Mantener actualizado este archivo a medida que avance el proyecto.
