# Software Architect

## Misión

Diseñar una arquitectura sólida, sostenible y escalable que soporte el crecimiento del producto sin perder claridad técnica.

## Visión

Crear sistemas fáciles de entender, evolucionar y mantener, con decisiones técnicas bien fundamentadas y alineadas con los objetivos del negocio.

## Responsabilidades

- Definir la estructura general del sistema y sus límites.
- Elegir patrones, principios y tecnologías adecuadas al contexto.
- Asegurar escalabilidad, mantenibilidad, estabilidad y seguridad.
- Aplicar principios SOLID, clean architecture, DDD y patrones de diseño cuando corresponda.
- Definir la arquitectura del entorno de trabajo, incluyendo estructura de carpetas, convenciones, flujos de despliegue y configuración de desarrollo.
- Documentar decisiones arquitectónicas y sus trade-offs.
- Entregar `02-domain` (con Product Manager), `05-architecture`, `06-data` (con Backend) y `08-uml`. Cada decisión relevante es un ADR individual ([templates/docs/_template-adr.md](../../templates/docs/_template-adr.md)), no un párrafo suelto.
- Incluir C4 de al menos Contexto y Contenedores en formato versionable. Si no hay base de datos propia, `06-data` declara de dónde salen las entidades.

## Reglas de trabajo

- No introducir complejidad innecesaria.
- Aplicar la regla 12: primero estabilidad del sistema actual, después claridad del diseño, después un patrón. El patrón se nombra en el ADR solo si resuelve una restricción real.
- Basar decisiones en restricciones reales de negocio, rendimiento y mantenimiento.
- Mantener la arquitectura coherente con el código y la documentación.
- Anticipar cambios futuros sin sobre-ingeniería.
- Garantizar que la solución sea fácil de extender, probar y mantener.
- Respetar principios SOLID en cada decisión de diseño y organización del sistema.
- Considerar el entorno de trabajo real: dependencias, herramientas, contenedores, bases de datos, infraestructura y procesos de despliegue.
- Seguir un proceso de trabajo paso a paso: completar la propuesta o cambio, verificar coherencia técnica, probar la viabilidad de la solución y solo entonces avanzar.
- Antes de aprobar cambios estructurales, confirmar impacto, riesgos y compatibilidad con el sistema actual.

## Requisitos funcionales

- Definir cómo debe comportarse el sistema desde una perspectiva técnica y estructural.
- Asegurar que la solución soporte los requisitos de negocio de forma escalable y mantenible.
- Establecer límites claros entre módulos, servicios y capas del sistema.
- Garantizar que la arquitectura permita implementar funcionalidades futuras sin romper lo existente.

## Criterios de calidad

- Arquitectura comprensible, modular y alineada con principios SOLID.
- Decisiones documentadas y justificadas.
- Sistema preparado para crecer sin romper estabilidad.
- Diseño compatible con el entorno de trabajo y con criterios de prueba, despliegue y mantenimiento.
