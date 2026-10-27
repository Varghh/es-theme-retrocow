# RetroCow para Batocera

Adaptación personal y liviana de **Minimal**, con Abstract como única apariencia y la identidad vaporwave de RetroCow para Pegasus.

**El tema original es obra de [lilbud](https://github.com/lilbud/es-theme-minimal), con el mantenimiento y las adaptaciones de [crcerror](https://github.com/crcerror/es-theme-minimal) y sus colaboradores.** Varghh es un aficionado que hace proyectos personales por hobby con ayuda de IA (vibecoding); su aporte aquí es la adaptación RetroCow. Todos los créditos, enlaces y condiciones originales se conservan abajo y en [CREDITS.md](CREDITS.md).

## Qué cambia

- **Solo Abstract:** se carga directamente, sin selector de fondos, estilos ni paletas. Una preferencia guardada de otra variante no puede cambiarlo. Las opciones generales de Batocera, como vista de lista o grilla, siguen siendo propias del frontend.
- Fondo Abstract adaptado a violetas, rosa y cian de RetroCow; PNG indexado de **1280×720**, reutilizado por todas las vistas. Se aplica un tinte neutro oscuro para facilitar la lectura.
- Mascota estática **256×229** y nombre **RetroCow** con la misma **Pixelify Sans** de Pegasus. Se mantienen las fuentes originales para listas, metadatos y menús.
- Colores de menús, marcos, selección e indicadores armonizados con RetroCow. Atribución visible a Minimal/lilbud/crcerror.
- Vista **detailed** por defecto y **grid** con carátula estática, sin componente de video. La vista estándar **video** conserva los videos para quien la seleccione expresamente; **basic** conserva su comportamiento original.
- Se desactivan reflejos del carrusel y de las carátulas y el brillo del título de la grilla. No se añaden animaciones, shaders, scripts, servicios ni dependencias de ejecución.
- Se retiran los cinco fondos alternativos y sus XML. Se conservan **los 130 recursos de sistemas sin cambios**, junto con el diseño, las posiciones de la lista y las funciones principales de Minimal.
- Ajustes automáticos de tipografía por debajo de 720 píxeles de alto para que el nombre, reloj y metadatos no se recorten por la ampliación de fuentes de Batocera. Comprobado visualmente a 800×600 y 1280×720 con el frontend de escritorio; detalles y límites en [VALIDATION.md](VALIDATION.md).

## Instalación y prueba

1. Copiar el contenido de este repositorio a `/userdata/themes/es-theme-retrocow/`, con `theme.xml` en la raíz de esa carpeta.
2. Reiniciar EmulationStation o recargar los temas y seleccionar **es-theme-retrocow** en los ajustes de interfaz de Batocera.
3. Empezar con la vista **detailed** o **basic** en equipos modestos. Si había una vista de video guardada por sistema, cambiarla manualmente; el tema no sobrescribe las preferencias generales de Batocera.
4. Revisar [VALIDATION.md](VALIDATION.md) y completar allí las pruebas en el equipo real antes de integrar el PR.

El tema no cambia resolución, VRAM, emuladores ni ajustes del sistema. La reducción de tamaño de los archivos y de las dimensiones del fondo es verificable; **no equivale a una medición de FPS o RAM en tu equipo**. Los videos seleccionados expresamente, las imágenes de la biblioteca y las transiciones configuradas en Batocera siguen influyendo en el consumo.

## Paleta

| Uso | Color |
| --- | --- |
| Base oscura / panel | `#0a0026` / `#1b1038` |
| Panel alternativo / borde | `#291747` / `#553ea8` |
| Nombre y acento rosa | `#ff71ce` |
| Selección / cian | `#7df9ff` |
| Texto principal / secundario | `#f5efff` / `#c1b3dc` |

El fondo raster contiene una adaptación de estos tonos; los colores de la interfaz se definen exactamente en el XML. La mascota y la fuente se reutilizan sin cambios del [proyecto RetroCow/Pegasus](https://github.com/Varghh/RetroCow-Amberline-).

## Créditos, licencia e historial

Se mantienen los avisos **Creative Commons CC-BY-NC-SA** del tema original, que no especifican versión; Pixelify Sans conserva su **SIL OFL 1.1** incluida. Ver [CREDITS.md](CREDITS.md) para autores, recursos y enlaces.

**El README original de crcerror se conserva íntegro a continuación.** Sus instrucciones sobre otras variantes, previews y la referencia histórica a 40 MB de VRAM describen Minimal; no son instrucciones actuales ni resultados de rendimiento medidos para RetroCow. Base: `7a9e5c50392015c50e233b66a1bda7a7916fcd52`.

---

# es-theme-minimal

**Words from the creator [lilbud](https://github.com/lilbud)**

> This theme is an attempt at making EmulationStation look more like a game system.

> Modern Game Systems (PS4, Xbox One, Switch, etc.) deliver a very specific experience compared to a computer. You turn it on, see a simple boot screen, and are in the menu in seconds. You know what you are getting in to. It's made abundantly clear that this is a video game machine. The games are front and center, and everything is wrapped up in a clean, minimal, interface...

> That is what I believe sets a game system apart from the Raspberry Pi. Sure, the interface is fast, and somewhat nice looking. But it doesn't feel like a video game system. This is where the Minimal theme steps in.

**This theme was made by lilbud / https://github.com/lilbud/es-theme-minimal**

---

# Abilities

This theme is super sleak and you can set VRAM to 40MB on a Raspberry system. \
So this is the smallest theme in foorprint as far as I know. \
\
This theme is highly customizable, you can change from **three** amazing layout by altering `theme.xml`\
Version 1 gets the original theme setting back as it was released 2017, whereas version 2 is a modernized layout in game list mode. Like the original author did, I decided to keep version 2 as default. The third option is a slighlty improved v1.

You can always add new backgrounds to the theme by adding a new file the `bg{x}.png` file, where x stands for a letter or digit. Next edit the `bg{x}.xml` file and add it's properties.

You can get rid off the "blurry" looking overlay by altering the overlay color inside the version assets, by removing the color code line.
```
		<image name="background" extra="true">
			<size>1 1</size>
			<pos>0 0</pos>
			<origin>0 0</origin>
			<path>./../assets/bg.png</path>
			<zIndex>0</zIndex>
			<color>10667f</color>
		</image>
```

# Changes

2019/06/05

Enabled help system, this is can be disabled/enabled into ES now
* 2026 - The Reawakening
  * Added video, grid and detailed view
  * Sorted things out - sleeker code
  * This thing is really held small and still werks with 40MB VRAM
* 2019/06/06
  * Added picture for Screenshots (BATOCERA/RECALBOX), own creation \
  * Added picture for ZX81, GX68000 and recolored Virtual Boy and Odyssey2 (=VIDEOPAC) \
  * Added picture for prboom (thx norbert79 from devianart for the B/W UAC graphics)
* 2019/06/07
  * Added background image from theme version 1.0 as default (the hexagons) \
  * Reencoded some files that were named as PNG but actually contained JPG.
* 2019/06/09
  * Added CPS1, CPS2, CPS3 system icons, recolored them (thank you anthonycaccese for your ArtBook theme) \
  * Readded Odyssey2 system icon, did some recoloring
* 2019/08/28
  * Added Solarus RPG system icon, recolored it (thank you to the Solarus Team designer, https://www.solarus-games.org/)
* 2019/10/04
  * Added OpenBOR system, ripped from RetroPie with some heavy recoloring

# Preview

Get in touch with the original theme author in [this thread via RetroPie Forum](https://retropie.org.uk/forum/topic/12435/)

### `V2.xml` theme (default)

![](https://i.imgur.com/KEEBkcO.png)

### `V1.xml` theme

![](https://i.imgur.com/5UR5yTF.png)

# Other things

Please give credits if you use this theme

* for example YOU @ https://github.com/DarrenCarol/Simple_Life (thx for nothing and taking all my SVGs but thx for your background pic that I've added now) - 14.02.2026