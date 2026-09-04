# Playbook: Etapa de calidad

## Propósito

Decirle al Orchestrator **cómo** cerrar calidad en un incremento, sin sustituir al QA Engineer ni inventar una suite que el entorno no soporta.

Los principios viven en [core/modules/quality-framework.md](../core/modules/quality-framework.md). El DoD está en [checklists/definition-of-done.md](../checklists/definition-of-done.md). Este archivo es la secuencia.

## Cuándo se ejecuta

Después de que la historia cumple DoR y hay autorización para implementar. No se espera a "el final del proyecto".

## Secuencia

### 1. Diseñar la prueba antes del código (QA + agente implementador)

- Cada criterio Gherkin de la historia tiene al menos un caso (feliz o error).
- Si no hay Gherkin, la historia no está Ready: vuelve a refinement. No se improvisan tests sobre prosa vaga.
- El nivel es proporcional al riesgo: regla de negocio y auth → test automatizado; copy o layout → verificación manual registrada.

### 2. Durante la implementación

- El implementador corre la prueba más barata que falle si la regla se rompe (unitaria del dominio, no un E2E de todo el SaaS).
- Un bug encontrado se corrige en el mismo entregable. No se abre un ticket para tapar un fallo que este PR introduce.
- Si el cambio toca API, datos o UI, living-docs tiene que pasar. Calidad y documentación no son etapas distintas.

### 3. Gate antes de Done

El Orchestrator pregunta, con evidencia:

- [ ] Criterios de aceptación verificados (auto o manual, con nota de cómo).
- [ ] Tests nuevos o actualizados si hubo lógica de negocio.
- [ ] Job de documentación viva en verde.
- [ ] Nada roto en el flujo ya operativo (regla 12: la estabilidad del vertical existente gana frente a una abstracción de test nueva).
- [ ] Deuda de prueba, si la hay, escrita en control de proyecto con fecha. No se esconde en el DoD.

### 4. Qué no es calidad

- "Pasa en mi máquina."
- Añadir Jest/Cypress/Playwright porque el catálogo del OS los menciona, sin un riesgo que lo pida.
- Pedir E2E completo cuando no hay entorno. Se documenta el riesgo y se verifica el contrato (API o unitario).

## Relación con la regla 12

1. **Estabilidad** — no fusionar si el flujo que ya opera queda sin evidencia.
2. **Clean code** — tests que nombran la regla de negocio, no la implementación.
3. **Patrones de test** (page objects, pirámide, contract testing) — solo cuando hay más de un consumidor o el E2E ya duele. No en el primer test del módulo.
