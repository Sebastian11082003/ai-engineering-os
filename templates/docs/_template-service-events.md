# Eventos — [Nombre del servicio]

> Si el servicio no publica ni consume eventos, dejar este archivo con una frase que lo declare. No borrarlo.

---

## Eventos que PUBLICA

| Evento | Topic / exchange | Cuándo se emite | Payload (campos clave) |
|---|---|---|---|
| [NombreEnPasado] | [topic.name] | [condición] | `{campo1, campo2}` |

### Esquema: [NombreEvento]

```json
{
  "eventId": "uuid",
  "eventType": "[NombreEvento]",
  "timestamp": "2026-01-01T12:00:00Z",
  "version": "1.0",
  "source": "[service-name]",
  "payload": {
    "[campo1]": "[tipo y descripción]"
  }
}
```

---

## Eventos que CONSUME

| Evento | Publicado por | Topic | Qué hace este servicio al recibirlo |
|---|---|---|---|
| [NombreEvento] | [servicio origen] | [topic] | [acción] |

---

## Garantías de entrega

| Garantía | Valor | Implicación |
|---|---|---|
| At-least-once | [Sí/No] | Los consumidores deben ser idempotentes |
| At-most-once | [Sí/No] | Pueden perderse eventos |
| Exactly-once | [Sí/No] | Más costoso, más fiable |

---

## Errores

- **Dead Letter Queue:** [nombre]
- **Reintentos:** [N, backoff]
- **Alertas:** [cuándo se avisa]
