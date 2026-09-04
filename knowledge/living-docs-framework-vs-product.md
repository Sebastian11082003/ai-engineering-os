# Lección: un mapa de living-docs por rol de repositorio

## Contexto

El job **Documentación viva** falló en el primer push completo de este OS (`c66ce8f`, 2026-09-03). El script clasificó `.github/workflows/ci.yml` como superficie `devops` de **producto** y exigió `docs/10-devops/**` y `docs/13-operations/**`. Esas carpetas son la convención SDD de un proyecto consumidor. El `docs/` de este repo documenta el framework, no un servicio desplegado.

## Qué se hizo

Se separaron las configs. El script no cambió.

- OS: `.living-docs.json` con `framework` y `framework-ci`.
- Producto: `templates/ci/living-docs.json` con backend / frontend / database / devops.

Un guard en CI impide que el mapa del OS vuelva a pedir `docs/10-devops`.

## Qué reutilizar

Si un repo no es un producto (librería, framework, monorepo de docs), no se le instala el template de consumidor. Se declara un mapa propio o se ignora la superficie que no existe. Copiar el JSON "completo" es el defecto.

## Referencias

- [standards/living-docs-ci.md](../standards/living-docs-ci.md)
- [playbooks/existing-project-adoption-playbook.md](../playbooks/existing-project-adoption-playbook.md)
- PR que cerró el falso rojo: merge `a4552b4` en `main`.
