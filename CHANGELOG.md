# Registro de cambios

Todos los cambios relevantes de ViuStream Pro se documentan en este archivo.

El formato sigue [Keep a Changelog 1.1.0](https://keepachangelog.com/es-ES/1.1.0/) y el
versionado sigue [SemVer 2.0.0](https://semver.org/lang/es/). Las versiones se publican como
instaladores firmados en [Releases](https://github.com/adancortes-ing/viustream-releases/releases).

## [No publicado]

Sin cambios todavía.

## [0.3.0] - 2026-11-16

### Añadido

- Inicio renovado: splash animado con progreso real y precarga; la ventana aparece con Inicio
  completo y sin solaparse con el splash.
- Descubrimiento configurable en Ajustes: de 3 a 10 filas, por géneros normalizados o por
  categorías del proveedor.
- Rotación de las filas de descubrimiento: diaria, en cada arranque o fija.
- Vista de lista detallada con sinopsis, dirección, reparto, progreso y metadatos en filas de
  altura fija.
- Filtros contextuales en «Ver todo»: se oculta únicamente el filtro que la fila de origen ya
  fija (género, colección o categoría).
- Refresco inmediato de las filas de usuario de Inicio (Continuar viendo, Favoritos y Ver
  después) al cambiar favoritos, vistos o progreso desde tarjetas, fichas o el reproductor.

### Cambiado

- Los filtros de Películas, Series y «Ver todo» se aplican solos: desaparece el botón
  «Aplicar filtros».
- Año y Década son excluyentes; elegir uno devuelve el otro a «Todos».
- «Quitar filtros» devuelve todos los criterios, incluido Orden, y recarga una sola vez.
- El mosaico desplaza una fila por muesca, mantiene un búfer de filas y reutiliza contenedores
  para sostener el desplazamiento en páginas grandes.
- El cambio entre filas, mosaico y lista deja una sola vista activa, con un único
  desplazamiento y sin perder filtros ni orden.
- Endurecimiento general: avisos de disco lleno, guardado de progreso más resistente y
  actualizaciones pendientes que sobreviven al reinicio.
- Accesibilidad e internacionalización: alto contraste del sistema, avisos anunciados al lector
  de pantalla, foco visible, reducción de movimiento, cultura regional y textos completos en
  español e inglés.

### Corregido

- El PiP ya no roba el foco al mostrar sus controles con el ratón.
- Las tarjetas que llegan con «Cargar más» descargan su portada.
- El arranque ya no muestra «Sin fuente» antes de cargar el contenido.
- El splash se cierra con Inicio completo y sin solapamiento con la ventana principal.
- Los errores de reproducción por contenedor o códec se explican con una causa y una acción.

### Seguridad

- La recuperación de la base local pone en cuarentena el archivo dañado y solo restaura una
  copia verificada.
- La actualización pendiente se descarta si esa versión ya está instalada, y el paquete se
  verifica por SHA-256 y Authenticode antes de aplicarse.

## [0.2.0] - 2026-11-09

### Cambiado

- Segunda versión de prueba: ejercicio del flujo de actualización completo desde 0.1.0, con
  conservación de perfiles, catálogo, listas y progreso.

## [0.1.0] - 2026-11-09

### Añadido

- Primera versión de prueba del instalador, con MSI para Windows x64 por usuario (sin permisos
  de administrador) y por máquina (con UAC).
- Actualizador integrado: descarga desde el canal estable, verificación SHA-256 y Authenticode,
  y manifiesto `update.json` con la versión, los paquetes y sus hashes.

[No publicado]: https://github.com/adancortes-ing/viustream-releases/compare/v0.3.0...HEAD
[0.3.0]: https://github.com/adancortes-ing/viustream-releases/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/adancortes-ing/viustream-releases/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/adancortes-ing/viustream-releases/releases/tag/v0.1.0
