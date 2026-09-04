# Plantillas de documentación

Copiar estos archivos al `docs/` del proyecto consumidor. No se rellenan aquí: este repositorio es el OS, no un proyecto de producto.

Convención de carpetas: [standards/documentation-structure.md](../../standards/documentation-structure.md).
Reglas de redacción: [standards/documentation-rules.md](../../standards/documentation-rules.md).
Secuencia: [playbooks/documentation-stage-playbook.md](../../playbooks/documentation-stage-playbook.md).

## Plantillas

| Archivo | Destino en el proyecto consumidor |
|---|---|
| [_template-adr.md](_template-adr.md) | `05-architecture/decisions/records/ADR-NNN-titulo.md` |
| [_template-hu.md](_template-hu.md) | historia en `04-requirements/` |
| [_template-service-readme.md](_template-service-readme.md) | `09-microservices/services/NN-nombre/README.md` |
| [_template-service-data-model.md](_template-service-data-model.md) | `.../data-model.md` |
| [_template-service-events.md](_template-service-events.md) | `.../events.md` |
| [_template-service-decisions.md](_template-service-decisions.md) | `.../decisions.md` |
| [_template-service-runbook.md](_template-service-runbook.md) | `.../runbook.md` |

## Árbol mínimo a crear en un proyecto nuevo

```
docs/
├── 00-governance/
├── 01-context/
├── 02-domain/
├── 03-product/
├── 04-requirements/
├── 05-architecture/decisions/records/
├── 06-data/
├── 07-api/contracts/openapi/
├── 08-uml/
├── 09-microservices/services/
├── 10-devops/
├── 11-quality/
├── 12-ux-ui/
├── 13-operations/
├── 14-training/
├── 15-project-control/
└── 99-archive/
```

Cada carpeta nace con un `README.md` de propósito. Los archivos de contenido se crean al llenarlos, no como placeholders vacíos.
