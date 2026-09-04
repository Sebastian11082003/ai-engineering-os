# FRAMEWORK_RULES

## Propósito

Este archivo contiene las reglas globales e inmutables del framework. Ningún agente debe romper estas normas, aunque el contexto del proyecto cambie.

## Reglas obligatorias

1. No escribir código ni implementar soluciones sin completar un análisis previo del problema, contexto y alcance.
2. No modificar la arquitectura sin una decisión documentada, justificada y trazable.
3. No cerrar una funcionalidad sin validación de calidad, documentación mínima y evidencia de revisión.
4. No asumir requisitos sin validarlos con el contexto del negocio o el proyecto.
5. No ignorar riesgos, bloqueos o dependencias; deben registrarse y gestionarse.
6. No avanzar a una nueva etapa si la anterior no quedó validada y documentada.
7. No introducir cambios irreversibles sin una estrategia de respaldo o mitigación.
8. No trabajar con información incompleta; el contexto debe ser suficiente antes de actuar.
9. No reemplazar la especialización de los agentes con decisiones improvisadas; el Orchestrator coordina, no sustituye.
10. No considerar un proyecto listo si no existe trazabilidad de decisiones, cambios y entregables.
11. No fusionar un cambio de backend, frontend, base de datos o infraestructura si la documentación afectada no se actualizó en el mismo entregable. La documentación viva se exige en CI, no en un checkbox.

## Principio de cumplimiento

Estas reglas deben ser interpretadas como límites operativos del sistema. Su cumplimiento es obligatorio para mantener la calidad, la estabilidad y la reutilización del framework.
