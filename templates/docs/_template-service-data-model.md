# Modelo de datos — [Nombre del servicio]

> Este servicio es el **dueño autoritativo** de los datos descritos aquí.
> Ningún otro servicio debe leer estas tablas o colecciones de forma directa.

---

## Motor

**Motor:** [PostgreSQL / MongoDB / Redis / etc.]
**Justificación:** [por qué es adecuado para este servicio]

---

## Esquema

### Tabla o colección: [nombre]

**Propósito:** [qué representa]

| Campo | Tipo | Nulo | Descripción | Restricciones |
|---|---|---|---|---|
| id | UUID | No | Identificador | PK |
| [campo] | [tipo] | [Sí/No] | [descripción] | [FK/Unique/Check] |
| created_at | TIMESTAMP | No | Creación | Default NOW() |
| updated_at | TIMESTAMP | No | Última modificación | |
| deleted_at | TIMESTAMP | Sí | Soft delete | NULL = activo |

**Relaciones:**
- `[campo_id]` → FK a `[tabla].[campo]` en [este servicio / otro servicio vía evento]

### Índices

| Nombre | Campos | Tipo | Justificación |
|---|---|---|---|
| idx_[tabla]_[campo] | [campo] | BTREE | Búsquedas frecuentes por [campo] |

---

## Decisiones de modelado

- **[Decisión]:** [por qué se hizo así]

---

## Migraciones

**Herramienta:** [Flyway / Liquibase / Alembic / Prisma / knex]
**Ubicación:** `src/migrations/`
**Convención:** `V[NNN]__[descripcion].sql`
**Rollback:** [¿se soporta? ¿cómo?]
