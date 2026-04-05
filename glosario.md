# Glosario SDD

Los términos que aparecen en el ebook, en orden de aparición lógica.

---

**Vibe Coding**
Forma de trabajar con IA donde describes lo que quieres a grandes rasgos y el agente decide qué y cómo construirlo. Efectivo para proyectos pequeños o exploración inicial. Se degrada cuando el proyecto crece y no hay artefacto de referencia compartido.

---

**Spec-Driven Development (SDD)**
Metodología donde la especificación de comportamiento es el artefacto primario del proyecto. El código implementa la spec. Los tests verifican la spec. La spec describe qué tiene que ser verdad, no cómo implementarlo.

---

**Spec**
Documento que describe el comportamiento esperado de una feature o componente. Describe qué hace el sistema y qué tiene que ser verdad cuando el trabajo esté hecho. No describe cómo implementarlo. Vive en el repositorio, se versiona con git, y se mantiene actualizada con el proyecto.

---

**PRD (Product Requirements Document)**
El nombre formal de la spec en el contexto de SDD. Tiene ocho secciones: Problem Statement, Solution, User Stories, Constraints, Acceptance Criteria, Out of Scope, Assumptions, e Implementation Notes. Target de longitud: ~500 palabras.

---

**Artefacto**
Algo que existe de forma independiente al proceso que lo generó y que sobrevive a la conversación. El código es un artefacto. La spec es un artefacto. Los artefactos no dependen de la memoria de nadie para mantener su valor.

---

**Grilling**
Sesión de preguntas antes de escribir el PRD. El agente hace preguntas sobre el comportamiento esperado de la feature. El humano responde. El objetivo es descubrir los huecos antes de que el agente los rellene con sus suposiciones durante la implementación.

---

**Acceptance Criteria**
Los criterios que definen cuándo el trabajo está hecho. Cada uno tiene que poder pasar o fallar. Describen un input o condición y un output o comportamiento observable. "Funciona correctamente" no es un criterio de aceptación — no puede fallar.

---

**Out of Scope**
Sección del PRD que lista explícitamente lo que no entra en esta spec. Sin esta sección, el agente implementa todo lo razonablemente relacionado con la feature. Con ella, los límites son claros y verificables.

---

**Assumptions**
Sección del PRD que documenta lo que se da por sentado sobre el estado actual del sistema: tecnologías existentes, esquemas de datos, presencia o ausencia de tests. Si una assumption es incorrecta, todo el código generado puede estar mal alineado con el sistema real.

---

**Constitution**
Archivo que captura los principios técnicos del proyecto: qué tecnologías están aprobadas, qué restricciones de seguridad son no negociables, qué estándares de código hay que seguir. El agente la aplica automáticamente en todo lo que genera. No confundir con CLAUDE.md, que contiene instrucciones de comportamiento.

---

**Vertical Slice**
Issue que implementa algo completo de punta a punta: interfaz, lógica, y datos, si aplica. Cuando está hecho, hay algo verificable. Contraste con la división por capas (issue de frontend + issue de backend), donde nada es verificable hasta que todos están hechos.

---

**Tracer Bullet**
El primer issue del tablero. Corresponde al unknown más arriesgado o incierto del proyecto: lo que tiene más probabilidades de cambiar el plan si resulta que no es técnicamente viable de la forma imaginada. Si algo va a romper las assumptions del PRD, es mejor descubrirlo en el issue uno.

---

**Blocking Relationship**
Dependencia de secuencia entre issues: un issue no puede empezar hasta que otro esté completado. Documentar blocking relationships permite identificar qué issues pueden ejecutarse en paralelo y cuáles no.

---

**Ralph Loop**
Patrón de execution loop donde el agente cicla por todos los issues del tablero de forma autónoma hasta que no quedan más. Efectivo para issues bien definidos en dominios conocidos. Riesgoso para issues con lógica de negocio compleja o assumptions difíciles de articular.

---

**GSD (Get Shit Done)**
Patrón de gestión de contexto entre sesiones. Al final de cada sesión, el agente documenta el estado: qué se completó, qué está en progreso, qué está pendiente, qué decisiones se tomaron. Al inicio de la siguiente sesión, el agente lee ese estado y continúa desde donde quedó.

---

**BMAD (Boilerplate-Minimum Agentic Development)**
Framework de orquestación para proyectos con múltiples agentes especializados trabajando en paralelo. Cada agente tiene un rol definido (research, especificación, implementación, QA) y un formato de artefacto que produce para el siguiente agente en la cadena.

---

**Greenfield**
Proyecto que empieza desde cero. Sin código existente, sin decisiones tomadas, sin deuda técnica. El contexto ideal para aplicar SDD desde el primer día con constitution, specs, y issues antes de escribir una línea de código.

---

**Brownfield**
Proyecto existente al que se añade SDD. El enfoque correcto es adopción gradual: especificar hacia adelante (las features nuevas) y documentar lo existente cuando se toca, no intentar especificar todo lo que ya existe antes de empezar.

---

**Living Spec**
Spec que el sistema actualiza automáticamente a medida que el código cambia. Contraste con la spec estática, que se actualiza manualmente. Plataformas como Intent (Augment Code) y Kiro implementan este modelo. Representa la dirección futura del ecosistema SDD.

---

**Spec Theater**
Anti-patrón donde los artefactos SDD existen pero nadie los usa como herramienta de pensamiento. Los PRDs se escriben para cumplir el proceso, no para pensar. Los issues se cierran sin verificar los criterios. El resultado es un equipo con proceso pero sin el beneficio del proceso.

---

**openSpec**
Formato ligero de spec para proyectos existentes o contextos donde SpecKit es overhead innecesario. Cuatro secciones mínimas: Qué hace, Qué no hace, Criterios de aceptación, Assumptions. Sin instalación, sin estructura de directorios nueva. El mismo método, menos ceremonia.

---

**GitHub SpecKit**
Herramienta open source para implementar SDD con estructura formal. Incluye comandos (`/speckit.specify`, `/speckit.plan`, `/speckit.task`, `/speckit.implement`, `/speckit.validate`) y comandos de calidad (`/speckit.clarify`, `/speckit.analyze`, `/speckit.checklist`). Soporte para más de 20 plataformas de agentes.

---

*Recurso del ebook [Spec-Driven Development](https://dominicode.com/spec-driven-development) — DominiCode*
