# Guía de Desarrollo para Tienda Online de Smartphones

Este documento resume los pilares fundamentales para construir una tienda online robusta, desde los aspectos técnicos de CSS hasta la funcionalidad esencial y recomendaciones de diseño.

## 1. Fundamentos Esenciales de CSS
Para una tienda moderna, el uso de CSS debe ir más allá de los estilos básicos. Estos son los conceptos clave utilizados en los diseños anteriores:

* **CSS Grid Layout:** Ideal para la estructura general de la página (layout) y la cuadrícula de productos. Permite crear diseños complejos como el panel de administración o la página de catálogo con filtros de forma sencilla.
* **Flexbox:** Perfecto para alinear elementos pequeños como botones, menús de navegación, controles de cantidad en el carrito y centrado de imágenes.
* **Variables CSS (`:root`):** Indispensable para mantener la consistencia de marca. Permite cambiar el color principal (azul), los tonos de gris y las fuentes en todo el sitio modificando una sola línea.
* **Positioning (`sticky`):** Vital para que los filtros del catálogo o el resumen del carrito se queden visibles mientras el usuario hace scroll.
* **Media Queries:** Para garantizar que la tienda sea totalmente **Responsive**. Los móviles son la principal fuente de tráfico en e-commerce.

## 2. Funcionalidades de una Tienda Online
Cualquier tienda profesional debe incluir, como mínimo, las siguientes capacidades:

| Funcionalidad | Descripción |
| :--- | :--- |
| **Navegación Intuitiva** | Menú con categorías (Apple, Samsung, etc.) y buscador. |
| **Filtrado y Clasificación** | Filtrar por marca, rango de precio, almacenamiento o color. |
| **Gestión de Stock** | Visualización de disponibilidad (En stock, Agotado, Pocas unidades). |
| **Carrito Dinámico** | Suma de subtotales, cálculo de impuestos (IVA) y gastos de envío en tiempo real. |
| **Proceso de Checkout** | Formulario de pago seguro y selección de dirección de envío. |
| **Historial de Pedidos** | Área de usuario para descargar facturas y ver estados de envío. |

## 3. Elementos Visuales Críticos (UI/UX)
* **Imágenes de Alta Calidad:** Los móviles se venden por la vista. Es necesario usar fondos neutros o "estilo de vida".
* **Llamadas a la Acción (CTA):** Botones como "Añadir al carrito" o "Comprar ahora" deben tener colores que contrasten con el resto de la página.
* **Indicadores de Estado (Badges):** Etiquetas de "Oferta", "Nuevo" o "Reacondicionado" ayudan a captar la atención.
* **Jerarquía Tipográfica:** El precio siempre debe ser fácil de encontrar (tamaño grande y negrita).

## 4. Recomendaciones para CSS Profesional
1.  **Mobile First:** Diseña primero para móvil y luego expande a escritorio. Es más fácil añadir elementos que quitarlos.
2.  **Uso de Sombras Suaves (`box-shadow`):** Evita sombras negras y pesadas. Usa tonos translúcidos (ej. `rgba(0,0,0,0.05)`) para dar profundidad sin ensuciar el diseño.
3.  **Transiciones Suaves:** Añade `transition: all 0.3s ease;` a los botones y tarjetas para que la interacción se sienta orgánica.
4.  **Optimización de Fuentes:** No uses más de dos familias de fuentes distintas (una para títulos y otra para cuerpo de texto) para no penalizar la velocidad de carga.
5.  **Accesibilidad:** Asegúrate de que el contraste entre el texto y el fondo sea suficiente para personas con visión reducida.

---
*Documento generado para el proyecto MobiStore - 2026*
