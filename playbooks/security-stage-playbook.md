# Playbook: Etapa de seguridad

## Propósito

Decirle al Orchestrator **cómo** revisar seguridad en un incremento, sin sustituir al Code Reviewer ni instalar un stack de seguridad que el producto no opera todavía.

Los principios viven en [core/modules/security-framework.md](../core/modules/security-framework.md). Este archivo es la secuencia. La calidad de pruebas está en [quality-stage-playbook.md](quality-stage-playbook.md); aquí se cubre auth, tenant, secretos y validación.

## Cuándo se ejecuta

En todo cambio que toque autenticación, autorización, datos de otro usuario/tenant, secretos, uploads, o entrada de red. No se espera a un “sprint de seguridad”.

Si el cambio es copy, layout o docs, este playbook no aplica. No se inventa un threat model para una etiqueta.

## Secuencia

### 1. Clasificar el riesgo (Orchestrator + implementador)

Antes de escribir código, una línea basta:

| El cambio… | Riesgo | Evidencia mínima |
|---|---|---|
| Lee o escribe datos de otro tenant / otro usuario | alto | test o prueba manual del rechazo (401/403/404) |
| Cambia login, JWT, roles o permisos | alto | caso feliz + caso de rol/permiso insuficiente |
| Expone un archivo, URL o campo nuevo al cliente | medio | lista de lo que **no** se serializa (hashes, API keys) |
| Recibe input de red (DTO, query, upload) | medio | validación de tipo/tamaño/whitelist |
| No toca auth ni datos ajenos | bajo | review normal; no se abre este playbook |

Si no se puede clasificar, se trata como alto hasta que alguien lo justifique.

### 2. Durante la implementación

- Mínimo privilegio: el endpoint declara rol o permiso. Un `@Public()` nuevo se justifica en el PR.
- El tenant (o el dueño del recurso) sale del **token o de la sesión**, no de un id que el cliente adivina.
- Secretos solo en env / secret manager. Un valor de producción no entra al repo ni a un log.
- Validar entrada en el borde (DTO/schema). No “confiar en el frontend”.
- Un hallazgo de seguridad se corrige en el mismo entregable. No se deja un hash o una key “para después”.

### 3. Gate antes de Done

El Orchestrator pregunta, con evidencia:

- [ ] La clasificación de riesgo está escrita (PR o control de proyecto).
- [ ] Si el riesgo es alto o medio: hay prueba de que el caso prohibido falla.
- [ ] No viajan secretos ni hashes en la respuesta (select explícito, no “borrar el campo a mano”).
- [ ] Living-docs en verde si cambió el contrato o la regla de acceso.
- [ ] Deuda de seguridad, si existe, tiene dueño y fecha. Un `TODO: secure this` no es un plan.

### 4. Qué no es seguridad

- Añadir WAF, API Gateway, Vault o rotación de JWT porque el framework de seguridad los menciona.
- Un checklist OWASP pegado sin relación con el cambio.
- Pedir pentest para un PR de una línea.
- Ampliar un `PermissionsGuard` a todo el monolito en un solo PR “para quedar bien”. Se cubre el endpoint que este incremento toca.

## Relación con la regla 12

1. **Estabilidad** — no fusionar un agujero de tenant o de auth. Tampoco se redefine el modelo de identidad de un SaaS que ya opera para lucir un patrón nuevo.
2. **Clean code** — la regla de acceso se lee en un guard o en un `select`, no en un comentario.
3. **Patrones** (RBAC fino, ABAC, mTLS, zero trust) — solo si hay más de un consumidor o un incidente que lo pida. El default es rol + tenant + validación de borde.
