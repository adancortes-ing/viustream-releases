# Registro de cambios

Todos los cambios relevantes de ViuStream Pro se documentan en este archivo.

El formato sigue [Keep a Changelog 1.1.0](https://keepachangelog.com/es-ES/1.1.0/) y el
versionado sigue [SemVer 2.0.0](https://semver.org/lang/es/). Las versiones se publican como
instaladores en [Releases](https://github.com/adancortes-ing/viustream-releases/releases), junto
al manifiesto de actualizaci├│n firmado.

## [0.5.3] - 2026-11-18

### Añadido

- Catálogo canónico de sagas: 274 entradas revisadas a mano, 239 publicables con el catálogo
  actual, títulos reales en español e inglés y mínimo de 3 obras por saga. Se permite que una
  obra pertenezca a más de una saga (por ejemplo, «Universo DC» y «Superman»).
- «Universo de Marvel» como una sola saga con todas sus películas, además de las sagas por
  personaje (Iron Man, Thor, Capitán América, Vengadores, Guardianes, Ant-Man y Wolverine).
- Limpieza de títulos en toda la interfaz: se retiran `[M2]`, `[M5]`, `*LAT*`, `(ENG)`, `(SUB)`,
  `(TV)`, `(2)` y `()`; `[REC]` y los títulos de una sola palabra se conservan.
- Restauración de títulos quitados de una saga desde «Títulos quitados», con «Olvidar» para
  los que ya no están en el catálogo.
- Copia previa `viustream.pre-f14c3.db` antes de purgar las sagas y colecciones anteriores.
- Versión 0.5.3 visible en la barra de estado, el splash y Ajustes › Acerca de.

### Cambiado

- Las sagas ya no se generan por raíz de título: salen del catálogo canónico aprobado. La
  primera ejecución tras actualizar purga las sagas automáticas y las colecciones manuales
  anteriores y las reconstruye; los datos de usuario se conservan.
- Migración 016 con `display_title`, supresiones y exclusiones de miembros.
- Colecciones: borrado de manuales, convertidas y canónicas; combos con etiqueta; selector con
  lista visible; refresco tras el recálculo sin reiniciar.
- Ajustes › Página de inicio: los dos primeros bloques dejan de tener panel gris.
- Splash: barra y texto dentro de la franja de la imagen, versión bajo el eslogan.

### Corregido

- El borrado de colecciones convertidas ya no queda bloqueado.
- Los filtros de colección muestran su etiqueta y no el nombre del tipo interno.
- La lista del selector de títulos se muestra cuando hay resultados.
- La tarjeta duplicada «Colecciones y sagas» desaparece de «Página de inicio».
- El splash ya no añade una franja semitransparente sobre la imagen.

### Seguridad

- `update.json` firmado con ECDSA P-256 + SHA-256; la app verifica la firma antes de parsear.
- Los MSI siguen sin Authenticode: SmartScreen puede avisar en la primera instalación. Verifica
  el SHA-256 publicado en `update.json`.

### Notas

- F15 (similares) se desarrolla en 0.6.0 y F16 («Me gusta» y recomendaciones) en 0.7.0.

## [0.4.1] - 2026-11-16

### Cambiado

- Versi├│n de verificaci├│n del canal firmado: la 0.4.0 detecta, descarga y aplica esta
  actualizaci├│n con el manifiesto firmado y el instalador sin Authenticode. Sin cambios
  funcionales.

## [0.4.0] - 2026-11-16

### A├▒adido

- `update.json.sig`: firma ECDSA P-256 + SHA-256 del manifiesto de actualizaci├│n, publicada
  junto a `update.json`.

### Cambiado

- Los instaladores y ejecutables se publican **sin firma Authenticode**. Windows puede mostrar
  ┬½Editor desconocido┬╗ o el aviso de SmartScreen al instalar; es esperado. Comprueba el SHA-256
  del MSI publicado en `update.json`.
- La actualizaci├│n autom├ítica verifica la firma del manifiesto antes de leerlo y, despu├®s, el
  SHA-256 del instalador. Si la firma o el hash no cuadran, se rechaza y se conserva la versi├│n
  instalada.
- Cada release publica cuatro archivos: los dos instaladores, `update.json` y `update.json.sig`.
- La 0.3.0 se sustituye una vez a mano por la 0.4.0, conservando perfiles, cat├ílogo, listas y
  progreso. A partir de la 0.4.0, las actualizaciones vuelven a ser autom├íticas.

### Seguridad

- El manifiesto firmado impide aceptar una actualizaci├│n manipulada aunque el repositorio
  p├║blico o la red est├®n comprometidos: sin la clave privada no se puede fabricar una firma
  v├ílida. Un replay de una release antigua ya firmada no se puede falsificar, pero la
  comparaci├│n de versiones y `MajorUpgrade` bloquean la bajada.
- La firma del manifiesto no sustituye a la reputaci├│n de SmartScreen ni protege la primera
  instalaci├│n manual; antes de instalar, verifica el SHA-256 publicado.

## [0.3.0] - 2026-11-16

### A├▒adido

- Inicio renovado: splash animado con progreso real y precarga; la ventana aparece con Inicio
  completo y sin solaparse con el splash.
- Descubrimiento configurable en Ajustes: de 3 a 10 filas, por g├®neros normalizados o por
  categor├¡as del proveedor.
- Rotaci├│n de las filas de descubrimiento: diaria, en cada arranque o fija.
- Vista de lista detallada con sinopsis, direcci├│n, reparto, progreso y metadatos en filas de
  altura fija.
- Filtros contextuales en ┬½Ver todo┬╗: se oculta ├║nicamente el filtro que la fila de origen ya
  fija (g├®nero, colecci├│n o categor├¡a).
- Refresco inmediato de las filas de usuario de Inicio (Continuar viendo, Favoritos y Ver
  despu├®s) al cambiar favoritos, vistos o progreso desde tarjetas, fichas o el reproductor.

### Cambiado

- Los filtros de Pel├¡culas, Series y ┬½Ver todo┬╗ se aplican solos: desaparece el bot├│n
  ┬½Aplicar filtros┬╗.
- A├▒o y D├®cada son excluyentes; elegir uno devuelve el otro a ┬½Todos┬╗.
- ┬½Quitar filtros┬╗ devuelve todos los criterios, incluido Orden, y recarga una sola vez.
- El mosaico desplaza una fila por muesca, mantiene un b├║fer de filas y reutiliza contenedores
  para sostener el desplazamiento en p├íginas grandes.
- El cambio entre filas, mosaico y lista deja una sola vista activa, con un ├║nico
  desplazamiento y sin perder filtros ni orden.
- Endurecimiento general: avisos de disco lleno, guardado de progreso m├ís resistente y
  actualizaciones pendientes que sobreviven al reinicio.
- Accesibilidad e internacionalizaci├│n: alto contraste del sistema, avisos anunciados al lector
  de pantalla, foco visible, reducci├│n de movimiento, cultura regional y textos completos en
  espa├▒ol e ingl├®s.

### Corregido

- El PiP ya no roba el foco al mostrar sus controles con el rat├│n.
- Las tarjetas que llegan con ┬½Cargar m├ís┬╗ descargan su portada.
- El arranque ya no muestra ┬½Sin fuente┬╗ antes de cargar el contenido.
- El splash se cierra con Inicio completo y sin solapamiento con la ventana principal.
- Los errores de reproducci├│n por contenedor o c├│dec se explican con una causa y una acci├│n.

### Seguridad

- La recuperaci├│n de la base local pone en cuarentena el archivo da├▒ado y solo restaura una
  copia verificada.
- La actualizaci├│n pendiente se descarta si esa versi├│n ya est├í instalada, y el paquete se
  verifica por SHA-256 y Authenticode antes de aplicarse.

## [0.2.0] - 2026-11-09

### Cambiado

- Segunda versi├│n de prueba: ejercicio del flujo de actualizaci├│n completo desde 0.1.0, con
  conservaci├│n de perfiles, cat├ílogo, listas y progreso.

## [0.1.0] - 2026-11-09

### A├▒adido

- Primera versi├│n de prueba del instalador, con MSI para Windows x64 por usuario (sin permisos
  de administrador) y por m├íquina (con UAC).
- Actualizador integrado: descarga desde el canal estable, verificaci├│n SHA-256 y Authenticode,
  y manifiesto `update.json` con la versi├│n, los paquetes y sus hashes.

[0.5.3]: https://github.com/adancortes-ing/viustream-releases/compare/v0.4.1...v0.5.3
[0.4.1]: https://github.com/adancortes-ing/viustream-releases/compare/v0.4.0...v0.4.1
[0.4.0]: https://github.com/adancortes-ing/viustream-releases/compare/v0.3.0...v0.4.0
[0.3.0]: https://github.com/adancortes-ing/viustream-releases/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/adancortes-ing/viustream-releases/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/adancortes-ing/viustream-releases/releases/tag/v0.1.0
