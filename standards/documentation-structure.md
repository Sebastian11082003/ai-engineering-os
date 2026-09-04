# Estándar de Estructura de Documentación

## Propósito

[core/modules/documentation-framework.md](../core/modules/documentation-framework.md) define el "qué" y el "por qué": SDD, documentos obligatorios y puertas de revisión. Este estándar define el "cómo": carpetas, artefactos y responsables.

Este archivo no reemplaza el módulo de documentación; lo aplica. Los principios viven en `core/`. La convención de carpetas vive aquí.

## Convención de carpetas

Todo proyecto consumidor organiza su documentación en una carpeta raíz (recomendado: `docs/`) con las siguientes secciones numeradas. El número indica orden de dependencia: una carpeta puede depender de las anteriores, no de las posteriores. `00-governance` envuelve todo el proyecto.

### 00-governance

Reglas del equipo: Git, convenciones ágiles, Definition of Ready, Definition of Done, reglas de documentación y seguridad.

- Artefactos mínimos: `README.md`, `definition-of-ready.md`, `definition-of-done.md`, `documentation-rules.md` (o referencia explícita a este estándar).
- Se lee **antes** del primer commit del proyecto.

### 01-context

Por qué existe el sistema: visión ejecutiva, alcance (dentro / fuera) y glosario.

- Artefactos mínimos: `overview.md`, `scope.md`, `glossary.md`.
- Equivale al discovery del Orchestrator (`software-lifecycle.md`, etapas 1-4). Si no existe, no se produce ninguna carpeta posterior.

### 02-domain

El problema de negocio: mapa de dominio, entidades, invariantes y eventos de dominio.

- Artefactos mínimos: `domain-map.md`, `entities-and-rules.md`, `domain-events.md`.
- En un proyecto pequeño el mapa puede ser un único bounded context. La ausencia de archivo no es proporcionalidad; la brevedad sí.

### 03-product

Qué construir: encuadre del problema, visión de producto y backlog inicial.

- Artefactos mínimos: `problem-framing.md`, `vision.md`.
- El backlog se prioriza (MoSCoW u otra técnica declarada). Roadmap y sprints se documentan como **estimación** hasta autorización explícita (`FRAMEWORK_RULES.md`, regla 1).

### 04-requirements

Qué debe hacer el sistema: historias de usuario, requisitos funcionales y no funcionales, matriz de trazabilidad.

- Artefactos mínimos: `user-stories.md`, `non-functional.md`, `traceability-matrix.md`.
- Historias en formato *Como / Quiero / Para que*, con criterios de aceptación en Gherkin (`Dado / Cuando / Entonces`). Plantilla: [templates/docs/_template-hu.md](../templates/docs/_template-hu.md).
- Cada historia indica de qué punto de `01-context` o `03-product` proviene.

### 05-architecture

Cómo se organiza el sistema: overview, ADRs, patrones y arquitectura hexagonal cuando aplique.

- Artefactos mínimos: `overview.md` (C4 Contexto y Contenedores como mínimo), `decisions/records/` con ADRs individuales.
- Plantilla: [templates/docs/_template-adr.md](../templates/docs/_template-adr.md).
- Cada ADR referencia el requisito o restricción que lo motiva.

### 06-data

Cómo se almacenan los datos: modelos, diccionario y estrategia de migraciones.

- Artefactos mínimos: `models.md`.
- Incluso sin base de datos propia: el archivo declara entidades de dominio y de dónde provienen.

### 07-api

Contratos de servicio: OpenAPI, autenticación y guías REST.

- Artefactos mínimos: contratos en `contracts/openapi/` **antes** de implementar endpoints (API-first).
- Si el proyecto no expone API, el README de la carpeta declara por qué no aplica.

### 08-uml

Diagramas de detalle: índice, secuencias de flujos críticos, componentes, ER.

- Artefactos mínimos: `diagram-index.md` y al menos un diagrama versionable (Mermaid u otra notación declarada) de los flujos críticos.

### 09-microservices

Catálogo de servicios o módulos y ficha de cada uno.

- Artefactos mínimos: `service-catalog.md` y, por cada servicio/módulo, la estructura de [templates/docs](../templates/docs) (`README.md`, `data-model.md`; `events.md` si hay eventos; `runbook.md` antes del primer deploy).
- En un monolito o landing, el catálogo tiene un único módulo. El nombre de la carpeta se conserva para no romper el índice; el contenido se adapta.

### 10-devops

Entornos, setup local, CI/CD y proceso de release.

- Artefactos mínimos: `local-setup.md`, `environments.md`, `ci-cd.md`.
- `local-setup.md` existe **antes** de escribir código de implementación.
- El pipeline de documentación viva es obligatorio: [living-docs-ci.md](living-docs-ci.md). El job debe ser status check requerido en `main`.

### 11-quality

Estrategia de pruebas, TDD cuando aplique, métricas y revisión de código.

- Artefactos mínimos: `testing-strategy.md` y criterios de aceptación consolidados desde `04-requirements`.
- La estrategia es proporcional al riesgo; no es una plantilla genérica sin relación con el contexto.

### 12-ux-ui

Sistema de diseño, mapa de navegación y flujos.

- Artefactos mínimos: `navigation-map.md`. `design-system.md` cuando hay interfaz de usuario.
- Si el proyecto no tiene UI, la carpeta declara por qué no aplica.

### 13-operations

Observabilidad, incidentes, SLA/SLO y runbooks de producción.

- Se completa de forma progresiva. Su ausencia de contenido en etapas tempranas no es una brecha; la carpeta sí debe existir.

### 14-training

Onboarding técnico, manuales de usuario y guías de administración.

- Artefactos mínimos: `technical-onboarding.md` cuando el equipo o un tercero deba operar el sistema.

### 15-project-control

Riesgos, dependencias, preguntas abiertas y backlog técnico.

- Artefactos mínimos: `risks.md`.
- Ningún riesgo, bloqueo o deuda se omite (`FRAMEWORK_RULES.md`, regla 5).

### 99-archive

Decisiones y documentos deprecados. No se borran: se mueven aquí con fecha y motivo.

## Principio de proporcionalidad: "proporcional pero no ausente"

No todos los proyectos requieren el mismo nivel de detalle. Un proyecto pequeño puede tener un ADR de un párrafo o un modelo de datos que diga "no hay base de datos propia; se usa el almacenamiento del proveedor X". Eso es válido.

Lo que no es válido es omitir el archivo en silencio. La proporcionalidad reduce contenido; no elimina la carpeta. Si un artefacto no aplica, el archivo existe y declara por qué.

## Principio de trazabilidad

Cada artefacto de una carpeta más específica rastrea su origen:

- Una historia en `04-requirements` apunta a `01-context` o `03-product`.
- Un ADR en `05-architecture` apunta al requisito o restricción que lo motiva.
- Un caso de prueba en `11-quality` apunta a la historia o NFR que cubre.
- Un cambio de API en `07-api` apunta al servicio dueño en `09-microservices`.

## Dependencias cruzadas

| Si cambia... | También se revisa... |
|---|---|
| Alcance (`01-context`) | Visión (`03`), requisitos (`04`), overview de arquitectura (`05`) |
| Una entidad de dominio (`02`) | Modelos (`06`), contratos (`07`), UML (`08`) |
| Un requisito funcional (`04`) | Criterios de aceptación, pruebas (`11`), historias |
| Arquitectura (`05`) | ADRs, servicios afectados (`09`) |
| Un modelo de datos (`06`) | Contrato del servicio dueño (`07`, `09`), ER (`08`) |
| Un contrato de API (`07`) | Servicio dueño y consumidores (`09`) |
| Un servicio (`09`) | Catálogo, eventos, matriz de datos |
| CI/CD (`10`) | Entornos y checklist de release |

## Mapeo de responsabilidad por agente

| Carpeta | Agente responsable |
|---|---|
| `00-governance` | Orchestrator, con consolidación del Documentation Engineer |
| `01-context` | Orchestrator (discovery) y Product Manager |
| `02-domain` | Software Architect y Product Manager |
| `03-product` | Product Manager |
| `04-requirements` | Product Manager |
| `05-architecture` | Software Architect |
| `06-data` | Software Architect y Backend Engineer |
| `07-api` | Backend Engineer |
| `08-uml` | Software Architect |
| `09-microservices` | Backend Engineer |
| `10-devops` | Backend Engineer / Frontend Engineer según el stack |
| `11-quality` | QA Engineer |
| `12-ux-ui` | UI Designer |
| `13-operations` | Documentation Engineer y Backend Engineer |
| `14-training` | Documentation Engineer |
| `15-project-control` | Orchestrator y Product Manager |
| `99-archive` | Documentation Engineer |
| Índice consolidado | Documentation Engineer |

El Orchestrator delega cada carpeta al agente responsable y valida el entregable antes de avanzar (`FRAMEWORK_RULES.md`, reglas 6 y 9). El Documentation Engineer no sustituye a los demás: consolida, cruza referencias y mantiene el índice.

## Correspondencia con la estructura previa (00–06)

Los proyectos que usaban la convención corta se migran así. No se mantienen dos estructuras en paralelo.

| Estructura previa | Estructura actual |
|---|---|
| `00-discovery` | `01-context` |
| `01-vision-alcance` | `01-context` + `03-product` |
| `02-requisitos` | `04-requirements` + `02-domain` |
| `03-gestion-proyecto` | `00-governance` + `03-product` + `15-project-control` |
| `04-arquitectura` | `05-architecture` + `06-data` + `07-api` + `08-uml` + `09-microservices` |
| `05-calidad` | `11-quality` |
| `06-operacion` | `10-devops` + `13-operations` + `14-training` |

## Relación con el resto del framework

- Principios SDD: [core/modules/documentation-framework.md](../core/modules/documentation-framework.md)
- Reglas de redacción: [standards/documentation-rules.md](documentation-rules.md)
- Ejecución: [playbooks/documentation-stage-playbook.md](../playbooks/documentation-stage-playbook.md)
- Plantillas: [templates/docs](../templates/docs)
- Checklists: [checklists](../checklists)
