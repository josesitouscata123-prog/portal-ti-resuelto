# Portal TI EA1

- **Código y nombre:** Portal TI - Nova Servicios
- **Curso y sección:** Desarrollo Web
- **Repositorio:** https://github.com/josesitouscata123-prog/portal-ti-resuelto
- **Solicitud de extracción:** N/A (Main Branch)
- **Preview:** Desplegado mediante Live Server / Vercel
- **SHA del commit evaluado:** 9905cba
- **Base utilizada:** Ejemplo resuelto semana 2 / Proyecto propio
- **Fecha de entrega:** 01/10/2026

---

## Inicio local

1. Abra la carpeta del proyecto en **Visual Studio Code**.
2. Abra el archivo `public/index.html` utilizando la extensión **Live Server** (o ejecute `npm start` / `scripts/serve.mjs` en la terminal).

---

## Estructura

- `public/`: Contiene el archivo HTML principal (`index.html`) y los archivos de la interfaz pública.
- `public/assets/`: Almacena las hojas de estilo CSS (`styles.css`), los scripts de interacción JavaScript (`ui.js`) y las imágenes o logos de la plataforma.
- `docs/`: Guía de actividades, plan de pruebas (`pruebas.md`) y capturas de pantalla con las evidencias visuales.
- `tests/`: Scripts de pruebas automatizadas e integración para el servidor (`server.test.mjs`).

---

## Cambios propios

| Cambio | Archivo | Qué recibí | Qué modifiqué | Evidencia o commit |
|---|---|---|---|---|
| Layout Responsivo | `public/assets/css/styles.css` | Anchos fijos rígidos que causaban desbordamiento | Media queries adaptativas para vistas de 320px, 768px y 1440px | Commit `9905cba` |
| Validación Formulario | `public/assets/js/ui.js` | Formulario estándar sin validaciones de cliente | Validación previa al envío e indicadores visuales de campos válidos/inválidos | Commit `9905cba` |
| Estilos e Interfaz | `public/assets/css/styles.css` | Controles de formulario e indicadores por defecto | Selectores de atributos, combinadores directos y estados `:focus-visible` | Commit `9905cba` |

---

## Correcciones verificadas

1. **Problema 1: Desbordamiento horizontal en pantalla móvil (320px)**
   - **Síntoma:** Aparecía barra de desplazamiento horizontal no deseada al navegar en dispositivos móviles.
   - **Evidencia anterior:** Captura del diseño a 320px mostrando tarjetas cortadas en el borde derecho de la pantalla.
   - **Causa:** Ancho fijo expresado en píxeles asignado a la clase `.service-card`.
   - **Cambio y archivo:** Se reemplazó el ancho fijo por `width: 100%` y límites de `max-width` responsivos en `public/assets/css/styles.css`.
   - **Commit:** `9905cba`
   - **Prueba repetida y resultado:** Inspección con DevTools a 320px de ancho; la interfaz se ajusta al viewport de manera completamente fluida y sin scrollbar horizontal.

2. **Problema 2: Indicador de foco inaccesible en navegación por teclado**
   - **Síntoma:** Al desplazarse con la tecla `Tab`, no era posible identificar cuál campo o botón estaba seleccionado.
   - **Evidencia anterior:** Ausencia de respuesta o resaltado visual en los controles enfocado por teclado.
   - **Causa:** Uso de `outline: none` en la hoja de estilos global sin reemplazo de accesibilidad.
   - **Cambio y archivo:** Se aplicó la pseudo-clase `:focus-visible` con un contorno personalizado `outline: 2px solid #0056b3` en `public/assets/css/styles.css`.
   - **Commit:** `9905cba`
   - **Prueba repetida y resultado:** Navegación secuencial por teclado; cada botón e input muestra un anillo de enfoque azul con alto contraste.

---

## Explicación de Selectores y Funcionalidades CSS

### 1. Selectores de Atributo Utilizados

- `input[type="radio"]`: Permite personalizar y dimensionar únicamente los controles de tipo radio button sin afectar los campos de texto estándar.
- `button[type="submit"]`: Aplica estilos específicos al botón de envío de formulario para diferenciarlo visualmente de otros botones o enlaces de la interfaz.
- `input:not([type="radio"])`: Utiliza la combinación del selector de atributo y la pseudo-clase de negación para aplicar dimensiones fijas de entrada a todos los campos excepto a los botones de opción.

### 2. Combinadores

- `.service-card > h3` (Combinador Hijo Directo): Garantiza que los estilos de encabezado se apliquen única y estrictamente a los títulos que sean hijos inmediatos de la tarjeta de servicio, evitando alterar títulos anidados en otros contenedores dentro de la misma.

### 3. Pseudo-clases con Propósito

- `:focus-visible`: Mejora la accesibilidad (a11y) mostrando un anillo de enfoque de alto contraste únicamente a los usuarios que navegan mediante teclado.
- `:required:valid` y `:user-invalid`: Proporcionan retroalimentación visual inmediata sobre la validez de los datos ingresados en el formulario antes del envío.
- `:disabled`: Ajusta el cursor y la opacidad del botón de envío cuando la interfaz requiere la interacción del usuario para habilitarlo.

---

## Decisión de Cascada y Especificidad

En la hoja de estilos `styles.css` se tomó una decisión explícita de especificidad para el diseño de la **Tarjeta de Servicio Destacada** (`.service-card--featured`).

### Caso de Estudio: Sobrescritura del Título en la Tarjeta Destacada

1. **Regla Base (Especificidad: 0, 0, 1, 1):**

css
.service-card > h3 {
color: var(--primary-color);
}

2. **Regla Destacada (Especificidad: 0, 0, 2, 1):**

css
.service-card.service-card--featured > h3 {
color: var(--accent-color);
}

- **Explicación:** La segunda regla prevalece sobre la base porque posee una especificidad superior al concatenar dos clases (`0, 0, 2, 1` frente a `0, 0, 1, 1`). Esto asegura que el título de la tarjeta destacada cambie de color sin necesidad de recurrir al uso de `!important`.

---

## Pruebas

Para revisar la matriz detallada de ejecución, casos de prueba de formularios y evidencias de capturas, consulte:
- `docs/pruebas.md`
- `docs/capturas/README.md`

---

## Apoyos y recursos

- **Código base:** Proyecto Portal TI - Ejemplo resuelto Semana 2.
- **Recursos gráficos:** Imágenes y recursos locales alojados en `public/assets/css/`.
- **Asistencia de IA:** Se utilizó asistencia de IA como soporte técnico en la estructuración de Markdown.

---

## Limitaciones

- **Formulario de demostración:** No envía ni guarda tickets en una base de datos real; valida la estructura del cliente en el navegador y simula la respuesta de la interfaz para pruebas.
