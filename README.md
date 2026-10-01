# Portal TI EA1

- Código y nombre:
- Curso y sección:
- Repositorio:
- Pull Request:
- Preview:
- SHA del commit evaluado: se registra en el texto de entrega del Aula Virtual, fuera de este archivo.
- Base utilizada: proyecto propio / proyecto base semana 2 / ejemplo resuelto
- Fecha de entrega:

## Inicio local

Abrir la carpeta con VS Code y public/index.html con Live Server. Indicar cualquier diferencia real de estructura.

## Estructura

Describir public/, assets/ y docs/ según el proyecto entregado.

## Cambios propios

| Cambio               | Archivo | Qué recibí | Qué modifiqué | Evidencia o commit |
| -------------------- | ------- | ---------- | ------------- | ------------------ |
| Contenido            |         |            |               |                    |
| HTML o CSS           |         |            |               |                    |
| Corrección de prueba |         |            |               |                    |

## Correcciones verificadas

Para dos problemas reales: síntoma, evidencia anterior, causa, cambio y archivo, commit, prueba repetida y resultado posterior. No inventar errores ni resultados.

## Decisión de cascada

Explica una regla CSS: qué selector aplica, con qué otra regla compite y por qué prevalece. Puedes localizarla durante la demostración.

## Pruebas

Ver docs/pruebas.md y docs/evidencias/.

## Apoyos y recursos

Declara el código base, recursos gráficos y ayuda de personas o IA. Para IA indica herramienta, solicitud y verificación realizada. Si no se usó, indícalo.

## Limitaciones

Formulario de demostración: no envía ni guarda tickets. Registrar pendientes reales.

# Portal de Soporte - Nova Servicios

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
   ```css
   .service-card > h3 {
     color: var(--primary-color);
   }
   ```
