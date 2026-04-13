# Capítulo 3: La spec como artefacto primario

> Este es un capítulo de muestra del libro **[Spec-Driven Development: Construye con IA sin Perder el Control](https://leanpub.com/sdd-spec-driven-development)** — de Bezael Pérez (DominiCode).

---

Hay una palabra en el título de este capítulo que merece un momento.

Artefacto.

No documento. No archivo. No entregable.

Artefacto.

En ingeniería, un artefacto es algo que existe de forma independiente al proceso que lo creó. El código es un artefacto. Los tests son artefactos. El ejecutable que se despliega en producción es un artefacto.

Todos tienen algo en común: sobreviven a la conversación que los generó.

Puedes cerrar el chat con el agente. Puedes irte de vacaciones dos semanas. Puedes incorporar a alguien nuevo al proyecto. El artefacto sigue ahí. Dice lo mismo que decía antes. No depende de que tú lo recuerdes.

La spec, cuando está bien hecha, es eso.

No es un resumen de lo que piensas hacer. Es la fuente de verdad de lo que estás construyendo.

---

## Por qué las specs tradicionales fallan

Si las specs son tan útiles, ¿por qué tienen tan mala reputación?

Por una razón sencilla: casi siempre llegan tarde.

En el desarrollo tradicional, la spec se escribe antes del código como requisito del proceso. Alguien del equipo de negocio redacta un documento de requisitos. El equipo técnico lo lee, asiente, y empieza a programar.

A mitad del proyecto, los requisitos cambian. Como siempre cambian.

¿Alguien actualiza la spec? Rara vez. Hay código que escribir. La spec queda obsoleta en semanas. Nadie la lee porque nadie confía en que refleje la realidad.

Al final, la spec describe un sistema que no existe. El código describe el sistema real. Y nadie sabe muy bien cómo llegaste de uno al otro.

Eso no es un problema de las specs.

Es un problema de cuándo se escriben y de quién es responsable de mantenerlas vivas.

---

## La spec viva

Una spec de SDD no es un documento de requisitos.

Es un contrato activo.

Vive en el mismo repositorio que el código. Se versiona con git. Cuando el comportamiento esperado cambia, la spec cambia primero. Después el código. Nunca al revés.

Eso tiene una consecuencia que parece pequeña pero no lo es: cualquier persona que abra el repositorio puede entender qué se está construyendo sin hablar con nadie.

El agente también puede.

De hecho, para el agente es todavía más valioso. Porque el agente no tiene contexto histórico. No estuvo en la reunión del lunes. No recuerda la conversación de la semana pasada. Cada sesión empieza desde cero.

La spec es lo que le da continuidad.

Sin spec, el agente trabaja con lo que tiene: el código actual y lo que tú le cuentes en el prompt. Con spec, el agente trabaja con el código actual, lo que le cuentes en el prompt, y la descripción completa de qué tiene que ser verdad cuando termine.

La diferencia en la calidad del output es inmediata.

---

## Comportamiento, no arquitectura

Aquí está el error más frecuente cuando alguien empieza a escribir specs.

Describe cómo se va a construir algo en lugar de qué tiene que hacer.

Hay una diferencia enorme entre estas dos frases:

*"El sistema usará JWT con RS256 y Redis para la invalidación de tokens."*

*"Cuando un usuario cierra sesión, no puede volver a usar el token anterior para acceder al sistema."*

La primera describe arquitectura. La segunda describe comportamiento.

La primera le dice al agente cómo implementar. La segunda le dice qué tiene que ser verdad.

¿Cuál es el problema de la primera?

Que si el agente sigue la instrucción al pie de la letra y resulta que JWT con Redis es overengineering para tu caso, nadie lo va a cuestionar. La spec lo pedía. El agente lo hizo.

Con la segunda, el agente elige cómo implementarlo. Puede elegir JWT, puede elegir sesiones en base de datos, puede elegir algo más simple. Lo que no puede hacer es saltarse el requisito: el token anterior tiene que quedar invalidado.

Una spec de comportamiento deja espacio para que el agente tome decisiones técnicas buenas.

Una spec de arquitectura convierte al agente en un ejecutor ciego de tus instrucciones, aunque esas instrucciones sean malas.

---

## Lo que tiene una spec y lo que no tiene

Una spec tiene seis cosas.

**Quién.** Quién usa el sistema y qué quiere conseguir. No un diagrama de actores. Una descripción de persona real con un problema real.

**Qué.** Qué puede hacer el usuario. Qué hace el sistema automáticamente. Qué pasa cuando algo falla. Verbos concretos: crear, eliminar, exportar, buscar.

**Cuándo.** El flujo. Los pasos exactos de cada acción principal. No a nivel de código, sino a nivel de experiencia. "El usuario hace clic en exportar. El sistema genera el archivo. El usuario lo descarga."

**Qué no.** Qué está fuera del alcance. Esta sección es la más ignorada y la más importante. Sin ella, el agente implementa todo lo relacionado con el tema. Con ella, los límites son claros.

**Qué debe ser verdad.** Los criterios de aceptación. Cada uno tiene que ser verificable. No "el sistema funciona correctamente". Sí "el archivo exportado contiene todos los registros del período seleccionado".

**Qué asumes.** Las assumptions. Qué das por sentado sobre el estado actual del sistema. Qué tecnologías ya existen. Qué no vas a cambiar en este ciclo.

Una spec no tiene estimaciones de tiempo. No tiene diagramas de secuencia. No tiene pseudocódigo. No tiene decisiones de arquitectura a menos que sean restricciones reales de negocio.

Si te encuentras escribiendo "vamos a usar X tecnología", para.

Pregúntate si es una restricción de negocio o una preferencia técnica.

Si es una preferencia, sácala de la spec. Ponla en notas de implementación, marcada claramente como sugerencia. El agente puede ignorarla si tiene mejor razón.

---

## El contrato entre tú y el agente

Hay una forma de pensar en la spec que lo aclara todo.

Es un contrato.

Tú defines el comportamiento esperado. El agente implementa algo que cumpla ese comportamiento. Cuando termina, verificas si lo que construyó coincide con lo que especificaste.

Si coincide: hecho.

Si no coincide: el agente no entendió la spec, la spec tenía un hueco, o las assumptions eran incorrectas. En cualquier caso, hay algo concreto que revisar. No es "no me gusta el resultado". Es "el criterio X no se cumple".

Esa diferencia importa.

Con vibe coding, cuando el resultado no te convence, la conversación es vaga. "No era exactamente lo que quería." "Falta algo." "No funciona como esperaba."

Con una spec, la conversación es precisa. "El criterio de aceptación número tres dice que el usuario puede exportar hasta diez años de datos. El sistema solo exporta un año."

El agente puede trabajar con eso. Con lo otro no puede.

---

## Cuánto tiempo lleva escribir una spec

Menos del que crees.

Una spec bien escrita para una feature de tamaño medio: entre veinte minutos y una hora.

Eso es lo que cuesta escribirla desde cero.

Pero hay un truco que multiplica la velocidad: el grilling.

No te sientes a escribir la spec solo. Primero le preguntas al agente que te haga preguntas. Le dices: "Voy a construir X. Antes de que escribamos la spec, hazme todas las preguntas que necesites para entender bien el comportamiento esperado. Mínimo diez preguntas."

El agente pregunta. Tú respondes. Y en esa conversación, la spec ya está tomando forma.

Cuando terminas el interrogatorio, tienes todo lo que necesitas para escribirla. O el agente la escribe basándose en tus respuestas y tú la corriges.

El grilling no es un paso opcional.

Es donde se descubren los huecos antes de que el agente los rellene con sus suposiciones.

Matt Pocock, uno de los desarrolladores que más público tiene en el ecosistema TypeScript, llegó a hacer sesiones de cuarenta y cinco minutos y cincuenta preguntas para features complejas. El resultado era una spec sin ambigüedad. El agente la ejecutaba sin desviarse.

Tiempo ahorrado en el grilling: cuarenta y cinco minutos.

Tiempo ahorrado en correcciones posteriores: días.

---

## La spec más corta que puedes escribir

Una spec tiene que tener suficiente para que el agente no tome decisiones que no le corresponden.

No más.

El error opuesto también existe: la spec kilométrica que intenta anticipar cada caso, cada excepción, cada detalle de implementación.

Hay datos sobre esto. Un estudio publicado en arXiv en 2026 analizó el impacto de la longitud de las especificaciones en la tasa de éxito de los agentes de IA. Los documentos largos reducían el task success rate en más de un veinte por ciento respecto a documentos concisos que cubrían lo esencial.

Más largo no es más claro.

Más largo es más ruido.

El target es alrededor de quinientas palabras para una feature de tamaño medio. Los detalles que no caben en quinientas palabras van en los issues hijos, cada uno con su contexto específico.

La spec es el mapa. Los issues son el GPS paso a paso.

Ambos son necesarios. Ninguno reemplaza al otro.

---

## Antes de seguir

Hasta aquí, la teoría.

Sabes qué es SDD. Sabes qué es una spec y qué no es. Sabes que describe comportamiento, no arquitectura. Que vive con el código. Que tiene seis partes. Que mide quinientas palabras, no cinco mil.

A partir del siguiente capítulo, empieza el método.

---

## El libro completo

Este capítulo cierra la Parte I. Lo que viene a continuación son las **7 fases del desarrollo con IA** — el método completo, con ejemplos reales y las plantillas listas para usar.

Los 10 capítulos restantes cubren:

- Las 7 fases: idea → investigación → prototipo → PRD → kanban → ejecución → QA
- Cómo escribir un PRD que la IA no malinterprete (con las 8 secciones exactas)
- De PRD a issues: vertical slices y tracer bullets
- El loop de ejecución: cuándo tú supervisas y cuándo el agente va solo
- GitHub SpecKit, openSpec y flujos agnósticos de herramienta
- Greenfield vs brownfield: qué cambia en proyectos existentes
- Los 5 anti-patrones que destrozan una spec (y cómo evitarlos)
- SDD en equipo

Más los apéndices: plantilla PRD completa, constitution template, checklist de calidad, glosario.

**[Consigue el libro completo → leanpub.com/sdd-spec-driven-development](https://leanpub.com/sdd-spec-driven-development)**

---

*[← Capítulo 2](cap-02-que-es-sdd.md) · [Índice](../README.md)*
