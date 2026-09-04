# [Nombre del servicio o módulo]

> Copiar a `docs/09-microservices/services/NN-nombre/README.md`.
> En un monolito o landing, este archivo describe el único módulo desplegable.

---

## Responsabilidad

[Una frase: qué hace y de qué datos es dueño autoritativo.]

---

## Ubicación en la arquitectura

| Campo | Valor |
|---|---|
| Número en el catálogo | [NN] |
| Puerto local | [80XX] |
| Repositorio | [URL] |
| Motor de datos | [PostgreSQL / MongoDB / Redis / —] |
| Comunica con | [servicios que consume] |
| Consumido por | [quién lo llama] |

---

## Lo que SÍ hace

- [Responsabilidad 1]
- [Responsabilidad 2]

## Fuera de alcance (lo que NO hace)

- [Qué delegó y a quién]

---

## Cómo ejecutarlo en local

```bash
# Desde la raíz del proyecto
docker compose up -d [service-name]

# Verificar
curl http://localhost:[puerto]/health
```

---

## Documentos relacionados

- [data-model.md](./data-model.md)
- [events.md](./events.md)
- [decisions.md](./decisions.md)
- [runbook.md](./runbook.md)
- Contrato API: `docs/07-api/contracts/openapi/[service-name].yaml`
