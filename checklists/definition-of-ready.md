# Definition of Ready (DoR)

Una historia está **Ready** cuando el equipo puede empezarla en el siguiente incremento sin resolver preguntas de fondo a mitad de trabajo. Si no cumple este checklist, vuelve a refinement. No entra a implementación (`FRAMEWORK_RULES.md`, reglas 1, 6 y 8).

Plantilla de historia: [templates/docs/_template-hu.md](../templates/docs/_template-hu.md).

## Checklist

### Claridad

- [ ] Está escrita como **Como [rol], quiero [acción], para [beneficio]**.
- [ ] El rol es específico (no "un usuario"; sí "un comprador autenticado").
- [ ] El beneficio es claro y verificable.
- [ ] Indica de qué punto de `01-context` o `03-product` proviene.

### Criterios de aceptación

- [ ] Hay al menos dos criterios en **Dado / Cuando / Entonces**.
- [ ] Cubren el camino feliz y los errores principales.
- [ ] Son testeables (se puede escribir una prueba para cada uno).
- [ ] No hay criterios ambiguos ("la respuesta debe ser rápida" no es válido).

### Dependencias

- [ ] Dependencias externas identificadas.
- [ ] Las bloqueantes están resueltas o tienen workaround documentado.
- [ ] Si depende de otra historia, esa historia está Done o en curso.

### Estimación

- [ ] El equipo estimó (puntos o talla).
- [ ] Cabe en un incremento. Si no, se partió.
- [ ] La fecha o sprint se documenta como estimación, no como compromiso, hasta autorización explícita.

### Preparación técnica

- [ ] Accesos y entornos disponibles, o el bloqueo está en `15-project-control`.
- [ ] Si hay endpoints nuevos, el contrato OpenAPI está definido (`07-api`).
- [ ] Si hay cambios de datos, el modelo está definido (`06-data` / ficha del servicio).
- [ ] El impacto en otros servicios o módulos está identificado.

### No funcionales

- [ ] Rendimiento, seguridad y observabilidad considerados cuando aplican, con métrica.

## DoR vs DoD

| | Ready (DoR) | Done (DoD) |
|---|---|---|
| Cuándo | Antes de empezar | Al cerrar |
| Quién verifica | Orchestrator + agente responsable en planning | Orchestrator + QA + agente responsable |
| Propósito | Poder empezar sin bloqueos de fondo | Entregar un incremento verificable |
