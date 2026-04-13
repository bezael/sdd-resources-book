# Capítulo 2: Qué es SDD (y qué no es)

> Este es un capítulo de muestra del libro **[Spec-Driven Development: Construye con IA sin Perder el Control](https://leanpub.com/sdd-spec-driven-development)** — de Bezael Pérez (DominiCode).

---

Hay una frase que resume todo lo que vas a leer en este libro.

La dijo IBM Technology en uno de los videos sobre el tema que más visualizaciones ha acumulado en los últimos meses:

*"La spec se convierte en el artefacto primario que dirige todo el trabajo posterior: implementación, tests, documentación, verificación."*

Una frase. Pero cambia el orden de todo.

En el desarrollo tradicional, el código es la fuente de verdad. La spec, si existe, sirve al código. Se escribe antes, se olvida después, y nadie la actualiza cuando las cosas cambian. Al final del proyecto, la documentación describe una versión del sistema que ya no existe.

Spec-Driven Development invierte esa relación.

La spec no sirve al código. El código sirve a la spec.

El código es el output. La spec es el artefacto. Y cuando terminas de construir, puedes verificar si lo que construiste coincide con lo que especificaste. No a ojo. De verdad.

Eso es SDD.

---

## Lo que no es

Antes de seguir, hay que limpiar algunos malentendidos. Porque cuando la gente escucha "especificaciones" piensa en ciertas cosas. Y casi todas son incorrectas.

**No es documentación que nadie lee.**

Todos hemos visto ese tipo de documentación. Cien páginas en Confluence que alguien escribió en 2021 y que nadie ha abierto desde entonces. Desactualizada, redundante, desconectada del código real.

Eso no es una spec. Eso es burocracia disfrazada de proceso.

Una spec de SDD vive con el código. Se versiona con el código. Cuando el proyecto cambia, la spec cambia. No al revés.

**No es waterfall.**

Waterfall significa que planificas todo al principio y luego ejecutas sin desviarte. El plan es el contrato y cualquier cambio es un problema.

SDD no dice eso.

La spec describe el destino, no el camino. Y el destino puede cambiar. Lo que no cambia es el principio: antes de que el agente ejecute, alguien tiene que haber pensado qué se quiere conseguir.

**No es lo contrario del vibe coding.**

Aquí está el malentendido más común.

SDD no es la alternativa seria y aburrida al vibe coding divertido y ágil. No te pide que abandones la velocidad que te dio la IA. Te pide que la uses en el sitio correcto.

El vibe coding tiene un problema de dirección. SDD pone la dirección.

La velocidad se queda.

---

## Cómo llegamos hasta aquí

SDD no apareció de la nada.

Viene de una tradición que lleva décadas intentando resolver el mismo problema: cómo hacer que el software sea verificable antes de que esté terminado.

El primer intento serio fue TDD. Test-Driven Development. La idea: escribe el test antes que el código. Si el test pasa, el código es correcto.

Funcionó. Pero los tests describen implementación, no comportamiento. Un test que verifica que la función `getUserById` devuelve un objeto no te dice si el usuario puede iniciar sesión o no. Describe el mecanismo, no la experiencia.

Entonces llegó BDD. Behavior-Driven Development. El test describe comportamiento desde el punto de vista del usuario:

*"Dado que soy un usuario registrado, cuando introduzco mis credenciales correctas, entonces accedo al dashboard."*

Mejor. Pero BDD sigue centrado en el test como artefacto principal. Y escribir tests de comportamiento para un agente de IA es complejo y frágil.

SDD da un paso más.

La spec describe comportamiento. El código la implementa. Los tests la verifican. Pero el artefacto central no es el test. Es la spec.

Y la spec puede escribirla alguien que no sabe programar.

Eso lo cambia todo.

---

## Por qué ahora

Thoughtworks, en su radar tecnológico de 2025, describió SDD como "una de las prácticas más importantes que emergieron con la IA generativa."

No es una opinión marginal.

GitHub SpecKit, una de las herramientas más conocidas para implementar SDD, tiene más de 72.000 estrellas en GitHub y soporte para más de veinte plataformas: Claude Code, GitHub Copilot, Amazon Q, Gemini CLI.

No es un proyecto de nicho. Es infraestructura.

Augment Code, uno de los agentes de IA para programadores más avanzados del mercado, construyó su flujo de trabajo completo sobre SDD. Su staff engineer lo dice sin rodeos: la sección de assumptions de la spec es donde pasan más tiempo iterando, porque es la que más impacto tiene en la calidad del código generado.

¿Por qué ahora y no antes?

Porque antes, las specs las leían desarrolladores humanos. Un desarrollador puede llenar huecos, hacer preguntas, pedir aclaraciones. Un agente no puede. Un agente rellena los huecos con lo que le parece más probable.

Y lo que le parece más probable no siempre es lo que tú querías.

Cuando el ejecutor es una IA, la calidad de las instrucciones importa más que nunca. SDD es la respuesta a eso.

---

## La tabla que lo resume

Hay muchas formas de explicar la diferencia entre vibe coding y SDD. Esta es la más directa:

| | Vibe Coding | Spec-Driven Development |
|---|---|---|
| Punto de partida | Prompt de implementación | Spec de comportamiento |
| El agente decide | Qué construir y cómo | Solo cómo. El qué ya está definido. |
| Resultado | Variable. Depende del prompt. | Verificable contra la spec. |
| Falla cuando | El proyecto crece | Las assumptions son incorrectas |
| Conocimiento del proyecto | En tu cabeza | En la spec |
| Cambio de decisión | Reimplementas desde cero | Actualizas la spec, el agente reimplementa |

La última fila es la que más gente ignora.

Cuando trabajas con vibe coding y una decisión de arquitectura cambia, normalmente hay que reescribir. No porque el código sea malo. Sino porque el código refleja una decisión que ya no es válida y nadie sabe exactamente dónde.

Con SDD, actualizas la spec. El agente reimplementa lo que cambió. Lo demás no se toca.

---

## Lo que SDD no resuelve

Sería deshonesto no decirlo.

SDD tiene un requisito previo que la gente suele ignorar: tienes que saber qué quieres construir.

Si tienes una idea vaga, una spec no la convierte en algo concreto. Solo la encapsula de forma más formal. Sigues sin saber qué quieres. Pero ahora está escrito en un documento bonito.

Una spec mal escrita produce código perfectamente ejecutado de algo que no querías.

El garbage in, garbage out de toda la vida.

SDD no reemplaza el pensamiento. Lo organiza.

Si estás explorando, si todavía no sabes cuál es la solución correcta, si necesitas construir para entender qué quieres construir, usa el prototipo. Esa es la fase 3 del método, y existe precisamente para eso.

Pero cuando ya sabes el destino, escríbelo. No lo guardes en tu cabeza. No lo des por supuesto.

Escríbelo.

---

## Una definición para quedarse con ella

Al final de todo, SDD es esto:

Defines el comportamiento esperado antes de que empiece la implementación. Ese comportamiento está escrito en un artefacto que el agente puede leer, seguir y contra el que puede verificar su trabajo.

El agente ejecuta.

Tú piensas.

Cada uno en su sitio.

Lo que viene en el siguiente capítulo es cómo se ve ese artefacto. Qué tiene, qué no tiene, y por qué la mayoría de la gente lo confunde con documentación cuando es exactamente lo contrario.

---

## Sigue leyendo

**[→ Capítulo 3: La spec como artefacto primario](cap-03-spec-como-artefacto.md)**

O consigue el libro completo con los 13 capítulos, las 7 fases del método, y las plantillas listas para usar:

**[Consigue el libro completo → leanpub.com/sdd-spec-driven-development](https://leanpub.com/sdd-spec-driven-development)**

---

*[← Capítulo 1](cap-01-vibe-coding.md) · [Índice](../README.md)*
