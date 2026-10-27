# Validación de RetroCow / Abstract

Base de Minimal: `7a9e5c50392015c50e233b66a1bda7a7916fcd52` (fork de crcerror). Esta revisión conserva la estructura de vistas de esa base; no pretende introducir compatibilidad con versiones antiguas que el tema original no soporta.

## Comprobaciones estáticas

- Los dos XML activos se analizan correctamente y el include de `assets/bg4.xml` se resuelve sin selección condicional. No quedan subsets ni fondos alternativos.
- Rutas locales de imágenes y fuentes verificadas; rutas dinámicas de logos `${system.theme}` e imágenes internas `:/` conservadas del tema original.
- Vistas resueltas: system, basic, detailed, grid, video, menu y screen. Todas las vistas de sistemas/juegos reciben la misma mascota, el nombre y los créditos.
- Detailed y grid resuelven `md_image`; basic, detailed y grid no declaran componentes de video. Video conserva la configuración de reproducción y fallback original.
- Los 130 archivos de `art/` y los ocho recursos comunes originales (tres fuentes, cuatro PNG y gamepad.svg) son idénticos byte por byte a la base.
- Las posiciones, dimensiones, espaciado y fuente de tamaño de la lista se conservan; reflejos y glow quedan en cero.
- Mascota, Pixelify Sans y OFL comparados byte por byte con RetroCow/Pegasus. Fuente estática válida, con todos los glifos de «RetroCow». PNG de mascota RGBA 256×229 y fondo PNG indexado 1280×720 decodifican correctamente.
- El README original se conserva íntegro como sección histórica. Los enlaces locales y avisos de autores se verifican; no se eliminan metadatos de autoría de los SVG.
- Nuevas propiedades contrastadas con `ThemeData::sElementMap` de [Batocera EmulationStation, revisión 47fa539](https://github.com/batocera-linux/batocera-emulationstation/blob/47fa539ad338020bab5e9e8ba87c4bb622806370/es-core/src/ThemeData.cpp). Esta comparación no equivale por sí sola a ejecutar el motor.
- Se corrige la alineación del reloj y se retiran dos propiedades de rating que el motor ignoraba (`alignment` y `maxsize`), conservando el tamaño de rating predeterminado. No quedan propiedades desconocidas en la comprobación contra ese esquema.

## Prueba con el frontend real

Se compiló Batocera EmulationStation **v42**, revisión `47fa539ad338020bab5e9e8ba87c4bb622806370`, como aplicación Linux de escritorio. Se ejecutó en Xvfb con OpenGL/Mesa llvmpipe y una biblioteca ficticia de tres entradas, dos sistemas y colecciones automáticas. No se distribuyen ROMs ni dependencias de prueba con el tema.

- **1280×720:** carrusel, vista básica, detallada, grilla, vista video sin clips (fallback a imagen), selección y menú principal.
- **800×600:** carrusel, vista detallada, selección, menú, carátula ausente y descripción ausente.
- La preferencia guardada `subset.background=Earth` se deja expresamente en la configuración de prueba: el tema sigue mostrando Abstract.
- Se verifican mascota, Pixelify Sans, créditos, fondo y selección. La prueba permitió corregir el orden de dibujo del encabezado del carrusel y los recortes causados por el aumento automático de fuentes por debajo de 720 píxeles de alto. Estos ajustes son automáticos por resolución y no crean variantes seleccionables.
- Capturas directas del framebuffer al presentar un cuadro completo, mediante instrumentación externa de prueba; no se modifica el motor que se distribuye ni se incorpora esa instrumentación al tema.
- La última carga no reportó propiedades desconocidas ni errores de análisis del tema. Los logs incluyen avisos del entorno (audio físico ausente, vsync no disponible y una consulta de red del frontend fallida), además de búsquedas PNG opcionales de logos cuyo SVG sí está presente.

Esto valida carga y presentación en ese frontend de escritorio. **No valida rendimiento en la PC de destino, reproducción de clips, audio, mandos físicos ni retorno desde emuladores reales.** Las capturas usan la mascota como carátula de prueba; las carátulas reales dependen de la biblioteca del usuario.

## Revisión del paquete instalable

- Se generó y extrajo un ZIP desde el árbol Git preparado para el PR. Los **147 archivos** del paquete coinciden con los archivos versionados; `theme.xml` queda directamente en la raíz de `es-theme-retrocow/`, junto con `art/` y `assets/`.
- La mascota está incluida en `assets/branding/retrocow-mascot.png`: PNG RGBA de 256×229 con transparencia real, idéntico al de RetroCow/Pegasus. Pixelify Sans, su licencia, las fuentes originales y el fondo están incluidos; no requieren instalación ni descarga adicional.
- Las rutas de los XML se resuelven dentro de la carpeta extraída o a recursos internos del frontend. Los 130 SVG se analizan correctamente y no contienen referencias `href` a archivos externos. El paquete no contiene enlaces simbólicos, archivos Git LFS, submódulos, cachés ni herramientas de compilación o prueba.
- Se cargó **la copia extraída**, en lugar del checkout de desarrollo, en el frontend real: basic y grid a 1280×720 y detailed a 800×600. Se verificaron carrusel, marca, navegación, menú y fallback de carátula/descripcion. Sin errores de análisis ni propiedades desconocidas del tema en esos logs.
- Se retiró `extra="true"` del fondo estándar en ambos XML: EmulationStation ya crea ese componente y el atributo provocaba otro fondo de pantalla completa. Se mantiene Abstract con la misma ruta, tinte y posición. No se alteraron las imágenes ni las fuentes durante esta revisión.
- El README explica la descarga de `master` **después del merge**, la extracción y el nombre final de la carpeta, y destaca la autoría original de lilbud, crcerror y colaboradores. Su texto histórico permanece íntegro.

## Tamaño y rendimiento

El contenido original versionado ocupa **7.233.980 bytes** (sin `.git`). La adaptación ocupa aproximadamente **2,67 MB**, documentación incluida: alrededor de **63 % menos**. Esto mide archivos distribuidos, no RAM ni FPS.

Abstract pasa de **360.292 a 95.535 bytes**. La imagen de origen pasa de 1920×1080 a 1280×720: una superficie RGBA sin comprimir tendría 8.294.400 frente a 3.686.400 bytes (55,6 % menos píxeles). Es una comparación teórica de la imagen de origen: el frontend puede escalar y cachear texturas según pantalla y configuración; no es una medición ni un límite de VRAM.

La mascota agrega 48.059 bytes y Pixelify Sans 51.100 bytes. Se reutilizan los mismos archivos en todas las vistas. No se añaden animaciones ni efectos. Las vistas detallada y grilla usan imágenes para evitar el componente de decodificación de video; si se elige la vista video, el consumo dependerá de los clips. No se cambian los límites de VRAM ni opciones globales de Batocera.

## Prueba pendiente en el equipo de destino

Antes de integrar el PR:

1. Instalar en una carpeta separada y seleccionar RetroCow. Comprobar que una selección anterior Earth/Vinyl/SimpleLife no reaparece y que no hay selector de variantes del tema.
2. Probar 16:9 y 4:3, o las resoluciones reales de uso: nombre RetroCow, mascota, créditos, reloj y actividad de mandos sin recortes ni superposiciones.
3. Navegar varios sistemas y bibliotecas grandes con teclado y mando. Comprobar selección, desplazamiento, menús y retorno desde un emulador real.
4. Probar basic, detailed y grid, con y sin carátula y descripción; probar además video con y sin clip. Verificar fallback y que detailed/grid no reproduzcan audio o video de los juegos.
5. Reiniciar EmulationStation y comprobar preferencias. Los ajustes globales o por sistema de vista/transiciones siguen bajo control del usuario.
6. Comparar con Minimal/Abstract en la misma máquina, resolución, biblioteca, VRAM y transiciones: arranque en frío, navegación, RAM/VRAM y fluidez. Registrar versión de Batocera, CPU, GPU, RAM y resultados. No se ha hecho un benchmark de hardware antiguo.

## Fondo y edición

Archivo integrado: `assets/bg4.png`. La herramienta integrada de imágenes se usó para adaptar los colores del Abstract original; después se redimensionó y codificó con ImageMagick a 1280×720 y 128 colores, sin dithering ni metadatos. El original permanece disponible en el historial Git y en el enlace de [CREDITS.md](CREDITS.md).

Prompt de edición: conservar el mosaico de hexágonos, su barrido diagonal y el espacio libre inferior/derecho; cambiar la base a `#0a0026`/`#1b1038`, los colores cálidos a `#ff71ce`/`#a83c86`, el cian a tonos basados en `#7df9ff` y los violetas a `#553ea8`/`#291747`; mantener aspecto 16:9, sin texto, mascota, logos ni nuevos elementos. La salida es una adaptación de la composición, no una recoloración matemática exacta.
