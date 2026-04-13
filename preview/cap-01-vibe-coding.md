# Capítulo 1: Vibe coding: funciona hasta que no funciona

> Este es un capítulo de muestra del libro **[Spec-Driven Development: Construye con IA sin Perder el Control](https://leanpub.com/sdd-spec-driven-development)** — de Bezael Pérez (DominiCode).

---

La primera vez que le pediste a una IA que te escribiera código, pasó algo raro.

Funcionó.

No a medias. No con errores raros que tardas horas en depurar. Funcionó de verdad. Pegaste el resultado, lo ejecutaste, y ahí estaba: haciendo exactamente lo que pediste.

Ese momento cambia algo en tu cabeza.

Porque llevas años programando con el mismo ritual: buscar en Stack Overflow, leer documentación que nadie actualiza, copiar un snippet que casi encaja pero no del todo, adaptarlo, romper algo, arreglarlo, romper otra cosa. Horas para lo que debería ser trivial.

Y de repente tienes una herramienta que lee tu mente.

Lo que vino después lo conoces. Empezaste a pedir más. Funcionalidades completas. Módulos enteros. Refactorizaciones que te daban pereza. Y el agente las hacía. Con una velocidad que todavía te parece irreal.

Eso tiene un nombre: vibe coding.

Lo acuñó Andrej Karpathy en 2025. La idea es simple: describes lo que quieres, el agente lo construye, tú revisas el resultado a ojo. Sin especificar demasiado. Sin planificar demasiado. Sin documentar nada. Confías en el modelo y en tu instinto.

Y funciona.

El problema es cuándo deja de funcionar.

---

## El proyecto que va bien hasta que no va bien

Imagina que estás construyendo una aplicación web. Algo razonable: autenticación, un dashboard, conexión a una API externa, algo de lógica de negocio.

Las primeras dos semanas son mágicas.

Cada sesión con el agente produce código real. Ves el proyecto crecer. Lo que antes te llevaba días, ahora lo tienes en horas. Piensas: esto es el futuro.

Tercera semana.

Pides un cambio en el módulo de autenticación. El agente lo hace. Pero algo en el dashboard deja de funcionar. Lo arreglas. Ahora hay un error en la API. Lo arreglas. Aparece otro en un sitio distinto.

No es un bug. Es una cadena.

Cuarta semana.

Preguntas al agente por qué eligió cierta arquitectura en el módulo de pagos. No lo recuerda. Cada sesión empieza desde cero. Las decisiones que tomaste hace diez días no existen para él.

Le pides que añada una funcionalidad nueva. La añade. Pero contradice algo que ya habíais decidido. El agente no lo sabe. Tú sí lo sabes, pero ya no tienes claro dónde está escrito.

Quinta semana.

El proyecto tiene cuarenta archivos. El agente empieza a alucinar dependencias que no existen. Propone soluciones que asumen una arquitectura distinta a la que tienes. Cada prompt necesita más contexto para que entienda qué está pasando.

Lo que antes tardabas una hora, ahora tarda tres.

Y lo más frustrante: el código funciona. Pero solo tú sabes por qué está así. Y ni siquiera estás seguro de acordarte de todo.

---

## Los tres síntomas

No todos los proyectos mueren igual. Pero el vibe coding que se sale de control tiene tres síntomas casi universales.

**El primero: el agente contradice al agente.**

Le pides algo hoy y lo hace de una manera. Se lo pides mañana, con otro contexto, y lo hace diferente. No porque haya cambiado el modelo. Porque no hay nada que ancle sus decisiones. Cada sesión es una hoja en blanco.

El resultado es un código que parece escrito por cinco personas distintas que nunca hablaron entre sí.

**El segundo: tú eres el único que sabe qué pasa.**

Todo el conocimiento del proyecto vive en tu cabeza. Por qué decidiste usar esa librería y no otra. Por qué el módulo de usuarios está separado así. Por qué hay ese workaround en la función de exportación.

Eso no es un problema hasta que te lo preguntan. O hasta que tú mismo te lo preguntas tres semanas después y no recuerdas la respuesta.

**El tercero: el contexto se come las sesiones.**

Cuando el proyecto era pequeño, el agente lo entendía todo. Ahora tienes que explicarle cada vez qué existe, cómo está estructurado, qué ya intentaste, qué no debes tocar.

Pasas más tiempo preparando el contexto que recibiendo código útil.

Si reconoces alguno de estos tres síntomas, no estás haciendo las cosas mal. Estás llegando al límite natural de una forma de trabajar que no estaba diseñada para crecer.

---

## Por qué pasa esto

El vibe coding tiene un problema de raíz.

No hay artefacto de referencia.

En el desarrollo tradicional, cuando alguien del equipo no sabe qué hace una función, puede leer el código. Cuando no entiende por qué se eligió cierta arquitectura, puede leer los commits, las decisiones técnicas documentadas, los comentarios.

El código es feo, pero es la verdad.

Con vibe coding, tienes código pero no tienes contexto. Tienes resultados pero no tienes decisiones. El agente produce, tú aceptas, y nadie escribe en ningún sitio por qué las cosas son como son.

Cuando el proyecto es pequeño, eso no importa. Caben todo en la cabeza: el tuyo y el del agente.

Cuando crece, todo se derrumba.

Porque el agente no tiene memoria entre sesiones. Cada vez que abres una conversación nueva, empieza de cero. Lo que construyó ayer no forma parte de su conocimiento hoy. Tienes que contárselo. Y si no tienes dónde buscarlo, se lo inventas. O lo omites. Y él rellena los huecos con sus mejores suposiciones.

Sus mejores suposiciones son buenas. Pero no son las tuyas.

---

## El error que casi todo el mundo comete

Cuando el proyecto empieza a dar problemas, la reacción habitual es una de estas dos:

La primera: intentar escribir prompts más largos y detallados. Explicarle al agente todo el contexto en cada sesión. Resultado: sesiones que tardan el doble y un agente que sigue sin entender del todo.

La segunda: rendirse y volver a programar a mano. "La IA no sirve para proyectos grandes." Resultado: pierdes la velocidad que habías ganado y no resuelves el problema de fondo.

Ninguna de las dos es la respuesta.

El problema no es el agente. El problema es que no tienes un artefacto que le diga, en cualquier momento, qué se está construyendo, por qué, y qué está permitido y qué no.

El agente es bueno ejecutando instrucciones claras.

Lo que falta son las instrucciones claras.

---

## No es un problema de IA

Antes de que existiera la IA generativa, los equipos de software tenían exactamente el mismo problema.

Un desarrollador nuevo entra al proyecto. Nadie le explica nada. El código está ahí, pero las decisiones detrás del código no están en ningún sitio. Empieza a hacer cambios que tienen sentido por separado pero rompen cosas que no debería romper.

¿La solución? Documentación. Especificaciones. Decisiones de arquitectura escritas. Criterios de aceptación.

No porque los desarrolladores sean malos. Sino porque los proyectos complejos necesitan un artefacto de referencia que exista fuera de las cabezas de quienes los construyen.

Con la IA, el problema es idéntico. Solo que más rápido.

El agente puede construir en horas lo que antes tardaba días. Pero si no hay un artefacto de referencia, los errores también se acumulan más rápido. El caos llega antes.

La solución no es menos IA.

Es más estructura.

---

## Lo que viene a continuación

Este libro trata de esa estructura.

Se llama Spec-Driven Development. SDD para abreviar.

No es una metodología compleja. No necesitas certificaciones ni consultores. No es lo contrario del vibe coding: es el upgrade.

La idea central es simple: antes de que el agente escriba una sola línea de código, existe un documento que describe qué se va a construir, por qué, y qué tiene que ser verdad cuando esté terminado.

Ese documento es la spec.

La spec es el artefacto de referencia que le faltaba a tu proyecto.

Con ella, el agente no rellena huecos. Ejecuta instrucciones. Y cuando termina, puedes verificar si lo que hizo coincide con lo que pediste.

No es volver al pasado. Es usar la IA como lo que es: una herramienta extraordinaria para ejecutar. No para decidir.

Las decisiones las tomas tú. Escritas. Antes.

Eso cambia todo.

---

## Sigue leyendo

El capítulo 1 describe el problema. Los siguientes 12 capítulos son el método completo.

**Capítulo 2:** Qué es SDD (y qué no es) — la definición exacta, de dónde viene, y por qué ahora.

**Capítulo 3:** La spec como artefacto primario — qué tiene, qué no tiene, y cómo escribirla en menos de una hora.

**[Consigue el libro completo → leanpub.com/sdd-spec-driven-development](https://leanpub.com/sdd-spec-driven-development)**

_13 capítulos. Las 7 fases del desarrollo con IA. Las plantillas listas para usar._

---

*[← Volver al índice de capítulos](../README.md)*
