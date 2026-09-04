# Playbook: Etapa de Documentación

## Propósito

Guía operativa para que el Orchestrator ejecute la documentación de cualquier proyecto con enfoque SDD ([core/modules/documentation-framework.md](../core/modules/documentation-framework.md)), sin omitir artefactos ni saltar puertas de revisión.

Este playbook no sustituye [standards/documentation-structure.md](../standards/documentation-structure.md): es la secuencia para producirla y validarla.

## Checklist ejecutable

### Fase 1 — Descubrimiento

#### 1. Verificar y completar `01-context`

Confirmar `overview.md`, `scope.md` y `glossary.md` (mínimo 10 términos clave). Si no existen o están incompletos, detener y completarlos primero (`software-lifecycle.md`, etapas 1-4). No se avanza sobre discovery sin validar (`FRAMEWORK_RULES.md`, reglas 6 y 8).

#### 2. Delegar dominio y producto

Citar explícitamente `standards/documentation-structure.md`:

- Software Architect + Product Manager → `02-domain`: mapa, entidades/reglas, eventos.
- Product Manager → `03-product`: problem-framing, visión, backlog inicial como estimación.

#### 3. Gate: validación del stakeholder

Confirmar con el stakeholder que el problema, el alcance (dentro/fuera) y los actores son correctos. Si no hay validación, no se abre la fase 2.

### Fase 2 — Definición

#### 4. Delegar requisitos al Product Manager

- `04-requirements`: historias con Gherkin, NFRs medibles, matriz de trazabilidad.
- Cada historia cumple [checklists/definition-of-ready.md](../checklists/definition-of-ready.md) antes de considerarse lista.
- Priorización MoSCoW u otra técnica declarada.

#### 5. Validar requisitos

- Existe visión, alcance y actores.
- Cada historia tiene origen, criterios de aceptación verificables y casos de error.
- Las reglas de negocio están en `02-domain`, no mezcladas como prosa suelta en las historias.
- Los NFR son medibles (no "el sistema debe ser rápido").

Si algo falta, detener y corregir. No se documenta la carencia como aceptable sin justificación explícita en el archivo correspondiente.

#### 6. Delegar arquitectura, datos y contratos

- Software Architect → `05-architecture`: overview C4 (Contexto y Contenedores), ADRs individuales.
- Software Architect + Backend Engineer → `06-data`: modelo conceptual y por servicio/módulo.
- Backend Engineer → `07-api`: contratos OpenAPI **antes** del código (API-first). Si no hay API, declarar por qué no aplica.

#### 7. Gate: revisión de arquitectura

- Cada decisión relevante tiene ADR propio.
- Existen C4 mínimos en formato versionable.
- Existe modelo de datos o justificación de por qué no aplica.
- Cada ADR referencia el requisito o restricción que lo motiva.
- Los contratos cubren las historias de la fase actual.

### Fase 3 — Diseño detallado

#### 8. Delegar detalle

- Software Architect → `08-uml`: índice y diagramas de flujos críticos.
- Backend Engineer → `09-microservices`: catálogo y ficha por servicio/módulo (plantillas en `templates/docs`).
- UI Designer → `12-ux-ui`: mapa de navegación y, si hay UI, sistema de diseño.

#### 9. Gate: planning de implementación

Confirmar que hay diseño suficiente para las historias del siguiente incremento. Completar esta fase **no autoriza** a implementar (`FRAMEWORK_RULES.md`, reglas 1 y 6). El Orchestrator pide autorización explícita al stakeholder.

### Fase 4 — Implementación y operación (solo con autorización)

#### 10. Antes del primer código de implementación

- `10-devops/local-setup.md` y `environments.md` existen y funcionan.
- QA Engineer → `11-quality/testing-strategy.md` proporcional al riesgo.
- Orchestrator → `00-governance` y `15-project-control/risks.md` actualizados.

#### 11. Durante la implementación

Cada cambio de comportamiento actualiza documentos en el mismo entregable ([documentation-rules.md](../standards/documentation-rules.md)). Una historia no se cierra sin [definition-of-done.md](../checklists/definition-of-done.md). El PR no se fusiona si el job **Documentación viva** falla ([living-docs-ci.md](../standards/living-docs-ci.md)).

#### 12. Delegar operación y continuidad

- Documentation Engineer + Backend Engineer → `13-operations` (progresivo; runbook antes del primer deploy).
- Documentation Engineer → `14-training/technical-onboarding.md` e índice consolidado.
- Orchestrator → riesgos, deuda y preguntas abiertas en `15-project-control`.

### Cierre de la etapa de documentación

#### 13. Checklist de completitud

El Orchestrator confirma uno por uno, con evidencia (archivo con contenido real, no placeholder), o con justificación escrita de por qué no aplica:

- [ ] Visión y overview
- [ ] Alcance con límites explícitos
- [ ] Glosario
- [ ] Mapa de dominio y reglas de negocio
- [ ] Actores del sistema
- [ ] Historias de usuario con criterios en Gherkin
- [ ] Requisitos no funcionales medibles
- [ ] Matriz de trazabilidad
- [ ] ADRs individuales
- [ ] Diagramas C4 (mínimo Contexto y Contenedores)
- [ ] Modelo de datos (o justificación)
- [ ] Contratos de API (o justificación)
- [ ] Catálogo de servicios/módulos
- [ ] Estrategia de pruebas
- [ ] Riesgos registrados
- [ ] DoR y DoD del proyecto
- [ ] Workflow de documentación viva activo y marcado como required check

Ningún ítem se marca completo sin el archivo correspondiente.

#### 14. Límite de alcance

Cerrar la etapa de documentación no es autorización para implementar. Esa decisión se pide por separado.

## Origen

Este playbook sustituye la secuencia corta 00–06. Incorpora las fases, puertas y orden de llenado del *Microservices Governance Framework* (CORHUILA), adaptados a las reglas y la proporcionalidad de AI Engineering OS. La brecha original (documentación incompleta al aplicar solo la lista de documentos obligatorios) sigue siendo el motivo de que este playbook exista.
