# Changelog

## Unreleased

- Playbook de seguridad por incremento: clasificar riesgo, tenant/auth desde el token, secretos fuera del cliente, evidencia del caso prohibido.
- Playbook para adoptar SDD en un proyecto existente (inventario + mapa + living-docs a medida, sin mover docs).
- Playbook de calidad por incremento (DoR → evidencia → DoD) para el Orchestrator.
- Knowledge: lección framework vs producto en living-docs. `knowledge/` entra a la superficie `framework`.
- Regla 12: ante un trade-off, priorizar siempre estabilidad, luego clean code, luego patrones de diseño (solo si reducen complejidad o habilitan escala).
- Separación de configs de documentación viva: el OS usa superficies `framework` / `framework-ci`; los proyectos consumidores siguen usando el mapa backend/frontend/database/devops de `templates/ci/living-docs.json`. Corrige el falso negativo de CI al tocar workflows del framework.
- Integración del enfoque SDD (estructura `docs/` 00–15, reglas de documentación, playbook con puertas de revisión, DoR/DoD y plantillas de ADR, historias y fichas de servicio), adaptado del Microservices Governance Framework (CORHUILA).
- Pipeline de documentación viva: un PR que cambia una superficie configurada no pasa CI si no actualiza los docs mapeados.
- Created the requested repository structure and starter documentation.
