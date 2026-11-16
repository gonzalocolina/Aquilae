# AQUILAE · Risk del Imperio Romano para el aula

Juego de estrategia por turnos en el navegador para repasar Historia de Roma y Latín jugando. La clase se divide en equipos que se reparten las provincias del Imperio Romano sobre un mapa real. Para conquistar una provincia enemiga, el equipo tiene que responder bien una pregunta de la materia.

**[▶ Jugar](https://gonzalocolina.github.io/Aquilae/)** · **[Creador de preguntas](https://gonzalocolina.github.io/Aquilae/editor/)** · **[Preguntas de ejemplo](ejemplos/preguntas-roma.json)**

![Mapa del Imperio Romano repartido entre cuatro equipos](docs/capturas/02-mapa.jpg)

## Contexto

- Diseñado dentro del **Proyecto de Investigación Docente *PhilHum Games***, para un **Trabajo Fin de Máster** del Máster en Educación.
- **Probado en el aula en 3 centros de Educación Secundaria y Bachillerato.**
- El profesorado no necesita saber programar: prepara sus preguntas con el editor incluido, las guarda en un archivo y las carga al empezar la partida. El mismo juego vale para cualquier tema o asignatura.

## Cómo se juega

1. Se eligen de 2 a 4 equipos y se cargan las preguntas.
2. Las provincias se reparten al azar y cada una empieza con 3 tropas.
3. En su turno, un equipo ataca desde una provincia con al menos 2 tropas a una provincia enemiga vecina, por tierra o por una ruta marítima.
4. Al atacar sale una pregunta. El docente muestra la respuesta y marca si el ataque ha tenido **éxito** o ha sido un **fracaso**.
5. Gana quien conquiste todo el Imperio. Si se acaban las preguntas, gana el equipo con más tropas.

La partida se puede guardar en un archivo y retomar en la siguiente clase.

| Inicio de partida | Pregunta durante un ataque |
|---|---|
| ![Pantalla de inicio](docs/capturas/01-inicio.jpg) | ![Pregunta y respuesta](docs/capturas/03-pregunta.jpg) |

### Creador de preguntas

Herramienta aparte para crear, editar, duplicar y validar bancos de preguntas, sin tocar código ni JSON a mano.

![Creador de preguntas](docs/capturas/04-editor.jpg)

## Detalles técnicos

- **HTML, CSS y JavaScript sin framework ni paso de compilación.** Cada herramienta es un único archivo HTML que funciona abriéndolo en el navegador, así que es fácil de usar en los ordenadores de un centro educativo.
- **Mapa con [Leaflet](https://leafletjs.com/)**, a partir de los datos GeoJSON de las provincias romanas de [klokantech/roman-empire](https://github.com/klokantech/roman-empire).
- **Vecindad entre provincias calculada con [Turf.js](https://turfjs.org/)** (`booleanIntersects`). Además hay conexiones marítimas, que se dibujan como rutas curvas y se comprueba que no atraviesen tierra.
- **Partidas guardadas y bancos de preguntas en JSON**, validados al cargarlos (formato, campos obligatorios, IDs repetidos). No hace falta servidor ni base de datos.
- **Despliegue automático en GitHub Pages** con GitHub Actions: el juego se sirve en `/` y el editor en `/editor/`.

### Formato de las preguntas

```json
[
  { "id": "roma-001", "pregunta": "¿Qué héroe es considerado el progenitor del pueblo romano?", "respuesta": "Eneas" },
  { "id": "roma-002", "pregunta": "¿De qué ciudad provenía Eneas?", "respuesta": "De Troya" }
]
```

El campo `id` es opcional. En [`ejemplos/preguntas-roma.json`](ejemplos/preguntas-roma.json) hay un banco de 249 preguntas sobre Roma, desde los orígenes hasta el Imperio.

## Estructura

```
Aquilae.html            Juego (carga las preguntas desde un archivo JSON)
editor-preguntas.html   Creador de preguntas
Aquilae Latín.html      Primera versión, con las preguntas integradas en el código
ejemplos/               Bancos de preguntas listos para usar
docs/capturas/          Capturas del README
```

## Autoría

- **Desarrollo:** Gonzalo Colina ([@gonzalocolina](https://github.com/gonzalocolina))
- **Diseño didáctico, preguntas y validación en el aula:** Juan Pérez González ([@Juaan51](https://github.com/Juaan51)), Proyecto de Investigación Docente *PhilHum Games*
