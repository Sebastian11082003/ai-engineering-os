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
- Puerta de CI de documentación viva: [standards/living-docs-ci.md](standards/living-docs-ci.md), script [scripts/check-living-docs.js](scripts/check-living-docs.js) y job **Documentación viva** en `.github/workflows/ci.yml`. El mapa de este repo es de framework (`framework`, `framework-ci`); el mapa de producto vive en [templates/ci/living-docs.json](templates/ci/living-docs.json).
- Prioridad operativa inmutable (regla 12): estabilidad → clean code → patrones de diseño.
- Playbooks operativos además de SDD desde cero: adopción en repo existente y calidad por incremento. Lección de CI en [knowledge/living-docs-framework-vs-product.md](knowledge/living-docs-framework-vs-product.md).

## Estado operativo

- La base conceptual del sistema está definida.
- La arquitectura modular del repositorio está implementada.
- El modelo de coordinación mediante Orchestrator ya está documentado.
- El sistema está listo para usarse como base de trabajo en nuevos proyectos.
- El framework fue puesto a prueba en un proyecto real (una landing page de servicios de software). La prueba evidenció una brecha entre el principio y la práctica: el Orchestrator, al aplicar solo una lista de documentos obligatorios, entregó documentación incompleta. Esa brecha se cerró primero con una estructura corta 00–06.
- La estructura corta se sustituyó por el enfoque SDD del *Microservices Governance Framework* (CORHUILA), adaptado a este OS: [core/modules/documentation-framework.md](core/modules/documentation-framework.md), [standards/documentation-structure.md](standards/documentation-structure.md), [standards/documentation-rules.md](standards/documentation-rules.md), [playbooks/documentation-stage-playbook.md](playbooks/documentation-stage-playbook.md). La proporcionalidad se conserva: no todos los proyectos son microservicios; ningún artefacto se omite en silencio.

## Prioridad de trabajo

Cualquier siguiente cambio (incluido alinear RestoOS al SDD) se evalúa con la regla 12. No se reescribe documentación ni se introduce un patrón nuevo si eso pone en riesgo un flujo que ya opera.

## Próximos pasos recomendados

- Aplicar [playbooks/existing-project-adoption-playbook.md](playbooks/existing-project-adoption-playbook.md) en RestoOS / NanaBurguer (`dev`): mapa SDD sobre docs actuales + living-docs ajustado. No reescribir.
- Playbook de seguridad del Orchestrator (aún no existe; calidad ya tiene secuencia).
- Revisar si otros módulos conceptuales presentan la misma brecha entre principio y práctica.
- Mantener actualizado este archivo a medida que avance el proyecto.
