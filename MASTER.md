# MASTER

## Objetivo

Este archivo es el punto de entrada principal para usar AI Engineering OS. Aquí se explica cómo navegar el framework, entender su estructura y trabajar con los agentes, equipos y procesos definidos en este repositorio.

## Cómo leer este framework

1. Comienza por [README.md](README.md) para entender la visión general del sistema.
2. Revisa [core/AGENTS.md](core/AGENTS.md) para entender la guía operativa central.
3. Usa [FRAMEWORK_RULES.md](FRAMEWORK_RULES.md) como la capa de normas obligatorias.
4. Consulta [PROJECT_STATE.md](PROJECT_STATE.md) para ver el estado actual del proyecto.
5. Usa [agents/management/orchestrator.md](agents/management/orchestrator.md) para entender el rol de coordinación.

## Estructura de uso

### 1. Comprensión del contexto

Antes de actuar, el equipo debe entender:

- el problema a resolver,
- el alcance,
- las restricciones,
- y el objetivo de negocio.

### 2. Selección del equipo adecuado

El Orchestrator decide qué equipo activar según la naturaleza de la tarea:

- Landing Team
- SaaS Team
- AI Team
- Backend Team
- Startup Team
- Ecommerce Team

### 3. Ejecución por etapas (SDD)

El flujo recomendado es:

1. análisis y discovery documentado (`01-context`, `02-domain`, `03-product`),
2. requisitos y arquitectura documentados (`04`–`07`),
3. diseño detallado (`08`, `09`, `12`),
4. autorización explícita,
5. implementación guiada por el diseño, con TDD y documentación viva,
6. validación (DoR/DoD) y cierre con trazabilidad.

La secuencia operativa de un proyecto **nuevo** está en [playbooks/documentation-stage-playbook.md](playbooks/documentation-stage-playbook.md). Si el repo ya existe, usar [playbooks/existing-project-adoption-playbook.md](playbooks/existing-project-adoption-playbook.md). Calidad de cada incremento: [playbooks/quality-stage-playbook.md](playbooks/quality-stage-playbook.md). La estructura de `docs/` está en [standards/documentation-structure.md](standards/documentation-structure.md). El merge de código exige el job de [standards/living-docs-ci.md](standards/living-docs-ci.md).

### 4. Validación obligatoria

Ninguna etapa debe cerrarse sin:

- contexto claro,
- revisión de calidad,
- documentación mínima con evidencia (no placeholders),
- y validación funcional o técnica.

## Regla principal

Este framework no debe usarse como una colección de instrucciones sueltas. Debe usarse como un sistema operativo de trabajo estructurado, con coordinación, reglas y trazabilidad.
