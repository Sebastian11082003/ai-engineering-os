# Framework de Desarrollo

## Propósito

Definir estándares generales de ingeniería aplicables a cualquier tecnología.

## Estándares clave

- Prioridad de implementación: estabilidad → clean code → patrones ([FRAMEWORK_RULES.md](../../FRAMEWORK_RULES.md), regla 12)
- Código limpio, modular y reutilizable
- Bajo acoplamiento y alta cohesión
- Manejo claro de errores y validaciones
- Organización de carpetas y responsabilidades
- Uso correcto de abstracciones e interfaces
- Control de versiones con Git
- Estrategias de branching y commits
- Revisión de código y refactorización continua
- Selección tecnológica basada en necesidad y contexto

## Relación con la documentación

El contrato de API se escribe **antes** del código (API-first). Un cambio de endpoint, modelo de datos o evento actualiza documentación en el mismo entregable. Ver [standards/documentation-rules.md](../../standards/documentation-rules.md).

## Regla de oro

La tecnología debe elegirse por contexto y necesidad, no por hábito.
