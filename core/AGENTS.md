# Core AGENTS

Este archivo funciona como la guía operativa central del AI Engineering OS.

## Objetivo

Unificar criterios de trabajo, arquitectura, calidad, documentación y colaboración para que este repositorio pueda reutilizarse en futuros proyectos sin perder consistencia.

## Capas de operación

### 1. Fundamentos del sistema

- [engineering-principles.md](engineering-principles.md): principios universales de ingeniería.
- [workflow.md](workflow.md): flujo de trabajo recomendado.
- [collaboration.md](collaboration.md): reglas de colaboración entre agentes.
- [communication.md](communication.md): estándares de comunicación.
- [decision-framework.md](decision-framework.md): base para decisiones técnicas y de producto.

### 2. Módulos conceptuales

- [modules/engineering-philosophy.md](modules/engineering-philosophy.md): filosofía de ingeniería.
- [modules/software-lifecycle.md](modules/software-lifecycle.md): ciclo de vida del software.
- [modules/architecture-framework.md](modules/architecture-framework.md): marco arquitectónico.
- [modules/documentation-framework.md](modules/documentation-framework.md): marco de documentación (SDD).
- [modules/development-framework.md](modules/development-framework.md): marco de desarrollo.
- [modules/quality-framework.md](modules/quality-framework.md): marco de calidad.
- [modules/development-framework.md](modules/development-framework.md): marco de desarrollo.
- [modules/quality-framework.md](modules/quality-framework.md): marco de calidad.
- [modules/project-management-framework.md](modules/project-management-framework.md): marco de gestión de proyectos.
- [modules/security-framework.md](modules/security-framework.md): marco de seguridad.
- [modules/performance-framework.md](modules/performance-framework.md): marco de rendimiento.
- [modules/knowledge-framework.md](modules/knowledge-framework.md): marco de conocimiento.

## Reglas operativas

- Todo cambio debe estar alineado con el objetivo del proyecto.
- Antes de implementar, se debe comprender el problema, el contexto y el alcance.
- Las decisiones técnicas deben documentarse y justificarse.
- La calidad, la seguridad y la documentación son obligaciones transversales.
- El sistema debe mantenerse preparado para ser clonado y reutilizado en otros contextos.

## Uso recomendado

Este documento debe leerse como la base del sistema, mientras que los archivos de agentes, equipos y módulos aportan profundidad, contexto y reglas específicas para cada especialidad.

La documentación de un proyecto consumidor se ejecuta con:

- [../standards/documentation-structure.md](../standards/documentation-structure.md)
- [../standards/documentation-rules.md](../standards/documentation-rules.md)
- [../playbooks/documentation-stage-playbook.md](../playbooks/documentation-stage-playbook.md)
- [../templates/docs](../templates/docs)

## Núcleo operativo

- [MASTER.md](../MASTER.md): guía para usar el framework.
- [FRAMEWORK_RULES.md](../FRAMEWORK_RULES.md): reglas globales obligatorias.
- [PROJECT_STATE.md](../PROJECT_STATE.md): estado actual del proyecto.
- [../agents/management/orchestrator.md](../agents/management/orchestrator.md): coordinación del equipo.

## Rol de coordinación: Orchestrator

El Orchestrator se incorpora como un componente transversal del sistema. Su función no es reemplazar a los especialistas, sino coordinar el flujo completo del trabajo: recibir solicitudes, seleccionar el equipo correcto, asignar contexto, validar entregables y mantener trazabilidad del proyecto.
