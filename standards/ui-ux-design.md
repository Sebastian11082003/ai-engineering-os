# Diseño UI/UX con referencias

Estándar obligatorio para todo proyecto consumidor que tenga interfaz. El objetivo es que la UI parezca diseñada para ese producto, no generada desde un prompt genérico.

Las fuentes de este documento son referencias para analizar, combinar y transformar. No son plantillas para copiar.

## Quién lo aplica

| Rol | Obligación |
|---|---|
| UI Designer | Produce la dirección de diseño antes de cualquier código de interfaz. |
| Frontend Engineer | Implementa esa dirección. No inventa una estética propia ni un layout por defecto. |
| Orchestrator | No autoriza implementación de UI si falta la dirección o si falla la evaluación. |
| Landing, SaaS, Ecommerce y Startup | Si el trabajo incluye interfaz, este estándar manda sobre el gusto del equipo. |

Si el proyecto no tiene interfaz, `docs/12-ux-ui/` declara por qué no aplica y este estándar no se ejecuta.

## Proyectos que ya tienen UI genérica

Un proyecto en curso no espera un rediseño total para cumplir. El siguiente incremento que toque interfaz abre con una dirección de diseño nueva para las pantallas afectadas. No se retoca color o radio de un layout genérico y se da por cerrado.

Señal de que hay que rehacer la dirección: al quitar logo y nombre, la pantalla podría pertenecer a otro producto.

## Antes de diseñar

Analizar y dejar por escrito:

- producto y qué debe hacer,
- usuario y la tarea que quiere terminar,
- industria,
- personalidad de marca,
- objetivo principal del usuario,
- objetivo de negocio,
- contenido real disponible,
- dispositivo y contexto de uso.

Sin ese análisis no hay composición. Un logo de restaurante sobre un dashboard SaaS genérico no es un diseño de producto.

## Cinco fuentes, cinco capas

No se copia un sitio. Se toma una capa de cada fuente y se sintetiza una composición original.

| Fuente | Capa | Pregunta |
|---|---|---|
| **Mobbin** | UX e interacción: navegación, flujos, móvil, dashboards, formularios, búsqueda, tablas, onboarding, ajustes, autenticación | ¿Cómo resolvería esta interacción un producto real de alta calidad? |
| **Godly** | Identidad visual: personalidad, hero, tipografía, layout, movimiento, narrativa visual | ¿Qué hace esta interfaz memorable? |
| **Web Anatomy** | Composición por sección: Hero, navegación, features, pricing, testimonios, CTA y equivalentes del producto | ¿Qué composición, densidad, ancla visual y comportamiento responsive tiene esta sección? |
| **Land-book** | Narrativa de producto y conversión: posicionamiento, jerarquía, prueba social, recorrido hacia la acción | ¿Cómo se comunica el valor de este producto en la pantalla? |
| **Google Stitch** | Exploración: al menos tres direcciones antes de elegir | ¿Cuál encaja con el producto, aunque no sea la más segura? |

Direcciones mínimas de exploración:

- Dirección A — mínima / editorial
- Dirección B — expresiva
- Dirección C — centrada en el producto

Elegir la que mejor encaja. No elegir por defecto la más convencional.

Cada sección elige su propio patrón. No repetir la misma estructura de tres columnas, tarjeta y botón en todo el flujo.

## Matriz de referencias

Antes del sistema visual, registrar la matriz. Cada fuente aporta patrones concretos de este producto, no una lista genérica.

```yaml
references:
  mobbin:
    purpose: UX / interacción
    patterns: []
  godly:
    purpose: identidad visual
    patterns: []
  web_anatomy:
    purpose: composición de secciones
    patterns: []
  land_book:
    purpose: narrativa y conversión
    patterns: []
  google_stitch:
    purpose: exploración
    directions: [A, B, C]
    selected: ""
```

Transformar significa combinar: la lógica de navegación de una referencia, el ritmo visual de otra y la tipografía de otra, en una composición propia. Reproducir una página completa es copia y no cumple este estándar.

## Design DNA

Todo componente sigue el mismo ADN. Si un bloque no cabe en este YAML, no entra en la interfaz.

```yaml
design_dna:
  visual_direction:
  typography:
  colors:
  layout:
  spacing:
  radius:
  shadows:
  imagery:
  icons:
  motion:
  density:
```

## Regla anti-genérica

El diseño falla si se puede describir solo como "un dashboard SaaS moderno" o "una landing moderna".

No usar por inercia:

- gradientes púrpura o azul como identidad,
- tarjetas muy redondeadas en toda la página,
- glassmorphism, sombras y pills sin función,
- layout por defecto de un framework (sidebar + navbar + grilla de tres cards),
- hero genérico con un solo botón,
- la combinación Inter + púrpura + blanco,
- la misma grilla de features en cada sección.

Esos recursos solo se permiten si el ADN del producto los justifica y la evaluación de originalidad sigue en 7 o más.

## Evaluación

Antes de implementar, puntuar:

```yaml
evaluation:
  UX_quality: 0-10
  visual_identity: 0-10
  originality: 0-10
  hierarchy: 0-10
  responsiveness: 0-10
  accessibility: 0-10
  product_fit: 0-10
```

Si `originality` es menor que 7, o `product_fit` es menor que 8, se rediseña. No se negocia con un ajuste de color.

Pregunta de cierre: si se quitan el logo y el nombre, ¿esta interfaz podría ser de otros cien productos? Si la respuesta es sí, se rediseña.

## Artefactos

Cuando hay interfaz, `docs/12-ux-ui/` incluye:

- `design-direction.md` — análisis de producto, matriz, tres direcciones, ADN, evaluación y qué hace único el diseño. Plantilla: [templates/docs/_template-design-direction.md](../templates/docs/_template-design-direction.md).
- `navigation-map.md` — mapa de navegación y flujos.
- `design-system.md` — componentes que obedecen el ADN.

El código de interfaz empieza después de que la dirección existe y la evaluación pasa. El orden prohibido es prompt → código.

## Pipeline

1. Entender el producto.
2. Analizar Mobbin, Godly, Web Anatomy y Land-book.
3. Explorar al menos tres direcciones (Stitch).
4. Extraer principios y escribir el ADN.
5. Componer wireframe.
6. Evaluar. Si falla, volver al paso 3.
7. Implementar el frontend contra el ADN.
8. Repetir la pregunta del logo sobre la interfaz construida, no solo sobre el documento.
