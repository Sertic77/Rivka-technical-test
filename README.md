# Collection Slider Solution

## Cómo probar
1.  **Iniciar entorno**: Ejecuta `shopify theme dev` en tu terminal.
2.  **Configurar**:
    - Abre el Editor de Temas desde el enlace generado.
    - Añade la sección **"Collection Slider"**.
    - Añade bloques **"Collection Item"** dentro de la sección.
    - Personaliza el contenido (título, descripción, botones) usando los bloques anidados por defecto.
3.  **Verificar**:
    - **Layout**: Comprueba la disposición: 1 item (móvil), 4 items (tablet/medio), 6 items (escritorio).
    - **Navegación**: Navega usando las flechas y verifica que el slider se desplaza **item por item** (gracias a la implementación de `single-step` y corrección de `scroll-snap`).

## Librería Elegida: Componente Nativo (`slideshow.js`)

En lugar de instalar una librería externa (como SwiperJS o Slick), **se reutilizó y extendió el componente `slideshow-component` nativo del tema**.

### Análisis Peso/Beneficio
*   **Peso Añadido: ~0 KB**.
    - No se descargan scripts ni estilos de terceros.
    - Solo se añadieron ~10 líneas de lógica JS y un archivo CSS ligero (~1KB) específico para la sección.
*   **Rendimiento (Performance)**:
    - Utiliza **CSS Scroll Snap** nativo. El desplazamiento es manejado por el navegador (compositor thread), lo que asegura 60fps incluso en dispositivos móviles gama baja, sin bloquear el hilo principal de JS.
*   **Beneficio**:
    - **Mantenibilidad**: Se integra perfectamente con la arquitectura existente del tema (eventos, accesibilidad, Custom Elements).
    - **Consistencia**: Mantiene la misma sensación y comportamiento (UX) que el resto de sliders de la tienda.
