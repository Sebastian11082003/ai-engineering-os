# Framework de Documentación

## Propósito

Convertir la documentación en un componente esencial del desarrollo, no en una tarea opcional. En este sistema la documentación **precede y guía** la implementación: no se documenta lo que ya se construyó; se diseña por escrito antes de escribir código.

## Enfoque: SDD (Software Design Documentation)

```
Tradicional:   Código  →  Documentación (si llega a existir)
SDD:           Documentación  →  Código  →  Documentación actualizada
```

### Principios SDD

1. **Diseño antes de código.** Un diseño documentado y validado es prerrequisito de la implementación. Si no está documentado, todavía no existe.
2. **Documentación viva.** Cada cambio de comportamiento actualiza los documentos afectados en el mismo entregable. Un documento desactualizado es un defecto.
3. **Trazabilidad.** Cada requisito tiene origen, cada historia tiene criterios de aceptación, cada criterio tiene evidencia de prueba, cada decisión tiene un ADR o equivalente.

Estos principios operacionalizan las reglas 1, 3, 6, 10 y 11 de [FRAMEWORK_RULES.md](../../FRAMEWORK_RULES.md).

## Documentos obligatorios

Todo proyecto consumidor debe cubrir, con proporcionalidad, estos tipos de documento:

- Visión, contexto y alcance
- Dominio, glosario y reglas de negocio
- Producto, backlog e historias de usuario
- Requisitos funcionales y no funcionales
- Arquitectura, ADRs y diagramas
- Modelo de datos y contratos de API
- Calidad, pruebas y Definition of Done
- Operación, onboarding y control de proyecto

La carpeta concreta, el artefacto y el responsable están en [standards/documentation-structure.md](../../standards/documentation-structure.md). Las reglas de redacción están en [standards/documentation-rules.md](../../standards/documentation-rules.md).

## Fases y puertas de revisión

```
Fase 1 — Descubrimiento     01-context → 02-domain → 03-product
Gate: validación del stakeholder

Fase 2 — Definición         04-requirements → 05-architecture → 06-data → 07-api
Gate: revisión de arquitectura

Fase 3 — Diseño detallado   08-uml → 09-microservices → 12-ux-ui
Gate: planning de implementación

Fase 4 — Implementación y operación
                            Código guiado por el diseño · TDD
                            10-devops · 11-quality · 13-operations · 14-training · 15-project-control
Gate: review + QA + autorización explícita para avanzar
```

Ninguna fase se cierra sin evidencia. Completar documentación **no autoriza** a escribir código: esa es una decisión separada (`FRAMEWORK_RULES.md`, reglas 1 y 6).

## Reglas de oro

- Un documento que nadie lee es un documento que no existe. Antes de crearlo: ¿quién lo lee, cuándo, y qué decisión permite tomar?
- Si el código cambió y el documento no, el documento está roto. Si el documento dice X y el código hace Y, el documento es una mentira.
- La proporcionalidad reduce el detalle, nunca elimina el artefacto en silencio. Si algo no aplica, el archivo existe y declara por qué.

## Aplicación práctica

- Estructura de carpetas y responsables: [standards/documentation-structure.md](../../standards/documentation-structure.md)
- Reglas de redacción, idioma y propietarios: [standards/documentation-rules.md](../../standards/documentation-rules.md)
- Secuencia operativa del Orchestrator: [playbooks/documentation-stage-playbook.md](../../playbooks/documentation-stage-playbook.md)
- Plantillas: [templates/docs](../../templates/docs)
- Checklists DoR / DoD / completitud: [checklists](../../checklists)
- CI de documentación viva: [standards/living-docs-ci.md](../../standards/living-docs-ci.md)

## Origen de la metodología

La estructura numerada, el flujo SDD, las puertas de revisión y el estándar por servicio se adaptan del *Microservices Governance Framework* (CORHUILA — Jesús Ariel González Bonilla), integrado aquí para que los agentes del OS lo ejecuten con las reglas, el idioma y la proporcionalidad de este repositorio.
