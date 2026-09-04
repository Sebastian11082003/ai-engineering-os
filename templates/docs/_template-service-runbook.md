# Runbook — [Nombre del servicio]

> Para quien opera el servicio bajo presión. Cada sección debe ser ejecutable: comandos concretos y responsable. Si un procedimiento no dice quién lo ejecuta ni cómo, no está completo.
> Obligatorio antes del primer deploy a staging o producción.

**Servicio:** [nombre]
**Repositorio:** [URL]
**Versión:** 1.0
**Última actualización:** YYYY-MM-DD

---

## 1. Información rápida

| Campo | Valor |
|---|---|
| Puerto local | [8001] |
| URL producción | [https://api.dominio.com/servicio] |
| URL staging | [https://staging.api.dominio.com/servicio] |
| Dashboard | [URL] |
| Canal de alertas | [canal] |
| Escalamiento | [nombre y contacto] |
| RTO objetivo | [30 min] |
| RPO objetivo | [5 min] |

---

## 2. Verificar salud

```bash
curl https://api.dominio.com/servicio/health
# Esperado: {"status": "ok", "version": "...", "db": "connected"}
```

---

## 3. Alertas frecuentes y qué hacer

### Tasa alta de 5xx

**Síntoma:** error rate > 2% durante 5 minutos.

```bash
# 1. Logs recientes
# 2. Estado de instancias
# 3. Eventos del último deploy
```

**Árbol de decisión:**
- Crash loop → reinicio controlado
- Errores de BD → sección 4.1
- Dependencia externa → sección 4.2
- Deploy reciente → evaluar rollback

---

## 4. Operaciones de mantenimiento

### Rollback

```bash
# Comando concreto del entorno del proyecto
```

### Migraciones

```bash
# Cómo se ejecutan y cómo se revierten
```

---

## 5. Comunicación en incidente

| Evento | Canal | Mensaje tipo |
|---|---|---|
| P0 detectado | [canal] | `[P0 START] [servicio] degradado desde [HH:MM]. Investigando.` |
| Resolución | [canal] | `[P0 RESOLVED] Duración: [X min]. Causa: [...]. Post-mortem: [fecha]` |

---

## 6. Post-incidente

- [ ] Servicio estable respecto al SLO
- [ ] Incidente registrado en `13-operations/`
- [ ] Stakeholders notificados
- [ ] Ticket de mejora en `15-project-control`
- [ ] Post-mortem agendado (si P0 o P1)
