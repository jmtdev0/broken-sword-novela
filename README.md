# Broken Sword: la novela

*La leyenda de los templarios, contada por George.*

Una novela corta en español que cuenta, en primera persona y con palabras propias, la historia del juego *Broken Sword: La leyenda de los templarios* (versión Reforged). Se escribe a medida que avanza una partida, así que de momento llega hasta el Hôtel Ubu.

## Leerla

- **En el navegador:** [jmtdev0.github.io/broken-sword-novela](https://jmtdev0.github.io/broken-sword-novela/). Es la novela entera en una sola página, con índice y modo oscuro, y recuerda por dónde vas. También puedes descargar [`Broken Sword - La novela.html`](Broken%20Sword%20-%20La%20novela.html) y abrirlo sin conexión.
- **En el móvil o en un lector:** descarga [`Broken Sword - La novela.epub`](Broken%20Sword%20-%20La%20novela.epub) (botón *Download raw file*) y ábrelo con Google Play Libros, Apple Books o cualquier lector EPUB. Para Kindle, envíalo con [Send to Kindle](https://www.amazon.com/sendtokindle).
- **Aquí mismo:** capítulo a capítulo.

## Capítulos

1. [Una terraza en otoño](capitulo-01.md)
2. [Un inspector, una periodista y un hombre con pico](capitulo-02.md)
3. [Bajo París](capitulo-03.md)
4. [Un hombre llamado Khan](capitulo-04.md)

## Una partida real

La novela no cuenta una partida ideal sacada de una guía, sino **una partida real**: la de quien la escribe. Antes de cada capítulo se leen el archivo de guardado y el registro que deja el juego, y la historia sigue lo que pasó en ellos:
- el orden real en que se visitaron los sitios;
- los objetos que se llevaban encima;
- con quién se habló, de qué y cuántas veces.

Por eso George le enseña dos veces la tarjeta de Rosso a Moue, pide tres veces que le lean el futuro y llama cuatro veces al sastre. Lo que el guardado no aclara se deja abierto, y la luz y el aspecto de cada sitio salen del propio juego.

### Cómo guarda la información Broken Sword Reforged

Lo que sigue se ha deducido examinando los archivos; no es documentación oficial.

En Windows, todo está en `%APPDATA%\Revolution Software\BS1R\`:

| Archivo | Qué es |
| --- | --- |
| `BS1R_ManualSave_N.sav` | Las partidas que guarda el jugador. |
| `BS1R_AutoSave_1.sav` … `_3.sav` | Tres autoguardados que se van turnando. |
| `BS1R_Log.txt` | Un registro con fecha y hora de casi todo lo que hace el jugador. |
| `vt7.ini` | Las opciones: volumen, idiomas, ayudas. |
| `steam_autocloud.vdf` | La marca de Steam Cloud, que sincroniza la carpeta. |

**El guardado (`.sav`)** pesa siempre 5.760 bytes: 1.440 números enteros de 32 bits, casi todos a cero. Reforged conserva el motor de guiones del juego de 1996, y a partir del entero 150 el archivo es el bloque de **variables de guion** del original, en el mismo orden. Los nombres de esas variables los publica [ScummVM](https://github.com/scummvm/scummvm/tree/master/engines/sword1), que reimplementó aquel motor. Con ellos, el guardado se puede leer:

- `SCREEN` es la pantalla en la que está George. Cada lugar tiene un número: la plaza del café es la 1, el piso de Nico la 10 y la recepción del Hôtel Ubu la 13.
- `POCKET_1` … `POCKET_52` son 52 casillas, una por cada objeto que George puede llevar, a 1 si lo lleva: la nariz roja, el pañuelo, las llaves de levantar…
- Cientos de marcas de conversación y de historia: si ya se ha hablado con alguien de un tema, cuántas veces o si ha pasado algo. Por ejemplo, `TODRYK_PLANTARD_FLAG` se pone a 1 cuando se le pregunta al sastre por Plantard.

Comparando los autoguardados entre sí se ve cuándo cambió cada cosa. Así se supo, por ejemplo, en qué momento se quedó Nico con el trozo de tela.

**El registro (`BS1R_Log.txt`)** es todavía más hablador. Cada línea lleva fecha, hora y categoría, y usa los mismos números que el motor. Estas son algunas, sin la fecha:

```
[17:16:02][UI]: Screen 10                ← entra en el piso de Nico
[17:17:28][UI]: Talk [18] with (129, 0)  ← le enseña el objeto 18 (las llaves de levantar) al personaje 129 (Nico)
[17:20:07][UI]: Subject [91] with (90, 1) ← por teléfono, saca el tema 91 (la fotografía)
[17:42:02][Save]: Write BS1R_AutoSave_2.sav (1:13:38 from chapter 0)
```

- `Screen` indica cada cambio de pantalla.
- `Examine` e `Interact` llevan la pantalla y el número del objeto.
- `Subject` es un tema de conversación y `Talk` es enseñarle un objeto a alguien.
- `Use … on` y `Combine` son las acciones con el inventario.
- `[Help]` son las pistas pedidas y `[Save]` los guardados, con el tiempo de juego.

Los personajes, los objetos y los temas se traducen con las tablas del motor original. Algunos ejemplos de personajes: el 129 es Nico, el 133 Rosso, el 145 Moue y el 146 Albert, el conserje.

## Aviso

Fan fiction no oficial, sin ánimo de lucro y sin relación con Revolution Software. *Broken Sword* y sus personajes pertenecen a sus propietarios. El texto de la novela es original: no reproduce los diálogos del juego.
