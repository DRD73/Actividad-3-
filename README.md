# Almacén Central — Panel de inventario

Dashboard administrativo para un sistema de gestión de inventario. Muestra el estado general de existencias, alertas de stock bajo, movimientos recientes de salida y el listado de productos, pensado para que un encargado de bodega revise su operación de un vistazo.

## Tecnologías usadas

- **HTML5 semántico** (`nav`, `header`, `main`, `footer`, roles ARIA)
- **CSS3** — Grid para el layout general, Flexbox para los componentes internos
- **Custom Properties (variables CSS)** para color, tipografía y espaciados
- **JavaScript vanilla** — únicamente para el menú colapsable en móvil
- Tipografías: *Space Grotesk* (encabezados) e *Inter* (texto y datos), vía Google Fonts

## Estructura del layout

```
┌─────────────┬───────────────────────────────┐
│             │            header             │
│   sidebar   ├───────────────────────────────┤
│             │             main              │
│             ├───────────────────────────────┤
│             │            footer             │
└─────────────┴───────────────────────────────┘
```

El layout principal se define con `grid-template-areas` (`sidebar`, `header`, `main`, `footer`). Dentro de cada área, los componentes (tarjetas, filas de tabla, menús, listas de alertas) usan Flexbox para alinearse y distribuirse.

## Componentes incluidos

1. **Barra lateral de navegación** con marca, enlaces y estado activo.
2. **Encabezado** con buscador, acción principal y avatar de usuario.
3. **Tarjetas de resumen** (referencias activas, stock bajo mínimo, valor en bodega, órdenes abiertas).
4. **Gráfico de barras** de salidas de la semana, construido en CSS puro.
5. **Panel de alertas prioritarias** de productos por debajo del mínimo.
6. **Tabla de productos** con filtros por estado y estados visuales (en stock / bajo mínimo / agotado).
7. **Pie de página** informativo.

## Decisiones de diseño

- **Paleta**: verde pino (`#3F6B5C`) como color de marca y acción, sobre un fondo cálido neutro (`#F1F0EC`), con ámbar (`#B8622E`) reservado exclusivamente para advertencias de stock bajo. Esto evita ambigüedad: el color siempre comunica un estado.
- **Tipografía**: Space Grotesk aporta carácter a los títulos sin sacrificar legibilidad; Inter se usa en tablas y datos por su claridad en tamaños pequeños.
- **Interactividad**: transiciones suaves en `:hover`/`:focus` sobre tarjetas, botones, filas de tabla y barras del gráfico, sin animaciones automáticas que distraigan.
- **Sidebar adaptable**: se reduce a solo íconos en tablet y se convierte en un panel deslizable activado por un botón de menú en móvil.

## Accesibilidad

- Uso de roles ARIA (`role="navigation"`, `role="main"`) y `aria-label` en íconos y botones sin texto visible.
- El botón del menú móvil usa `aria-expanded` y `aria-controls`, y el menú puede cerrarse con la tecla `Escape`.
- El gráfico de barras incluye una descripción alternativa mediante `role="img"` y `aria-label`.
- Estados de foco visibles (`:focus-visible`) en todos los elementos interactivos para navegación por teclado.
- Contraste verificado entre texto e íconos sobre sus fondos (verde pino oscuro con texto claro en la barra lateral; texto oscuro sobre fondos claros en el resto del panel).
- Se respeta `prefers-reduced-motion` para desactivar transiciones si el usuario lo solicita en su sistema.

## Responsividad

| Punto de quiebre | Comportamiento |
|---|---|
| Escritorio (> 1024px) | Layout completo con sidebar expandida |
| Tablet (681px–1024px) | Sidebar colapsada a solo íconos; tarjetas en 2 columnas |
| Móvil (≤ 680px) | Sidebar oculta y accesible como panel deslizable; tarjetas y contenido en una columna; columnas secundarias de la tabla ocultas |

## Capturas de pantalla

Ver carpeta `/evidencias` con capturas en escritorio, tablet y móvil.

## Cómo verlo localmente

Abrir `index.html` en cualquier navegador — no requiere servidor ni build.
