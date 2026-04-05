# Checklist de calidad antes de ejecutar

Usa esta lista antes de darle al agente el ok para empezar.

Cinco minutos ahora. Horas ahorradas después.

---

## Checklist del PRD

**Problem Statement**
- [ ] Describe el problema, no la solución
- [ ] Tiene menos de 3 frases
- [ ] Dice por qué importa ahora (urgencia, consecuencia, contexto)

**Solution**
- [ ] Describe comportamiento, no implementación
- [ ] No menciona tecnologías específicas (a menos que sean restricciones reales)
- [ ] Alguien no técnico puede entenderla

**User Stories**
- [ ] Tienen el formato: Como / Cuando / Entonces
- [ ] Hay 6 o menos (si hay más, probablemente son dos features)
- [ ] Cada una describe una acción concreta, no un estado vago

**Constraints**
- [ ] Son restricciones reales, no preferencias
- [ ] Si se viola una, el resultado es inválido independientemente del resto
- [ ] Si no hay restricciones reales, la sección está vacía (no rellena con obviedades)

**Acceptance Criteria**
- [ ] Cada criterio puede pasar o fallar — hay una acción y un resultado observable
- [ ] No hay criterios vagos: "funciona correctamente", "es intuitivo", "es rápido"
- [ ] Cubren los flujos principales Y los flujos de error
- [ ] Son verificables manualmente sin necesidad de leer el código

**Out of Scope**
- [ ] Tiene al menos 3 entradas
- [ ] Incluye las cosas más obvias que alguien podría asumir que entran
- [ ] Cada entrada especifica cuándo o dónde va (fase 2, issue separado, fuera del alcance)

**Assumptions**
- [ ] Reflejan el estado real del sistema que el agente va a encontrar
- [ ] Cubren: tecnologías existentes, esquemas de datos, presencia/ausencia de tests
- [ ] No son obviedades — son cosas que, si el agente las asume mal, el resultado está mal
- [ ] Alguien que no conozca el proyecto las entendería

**Implementation Notes**
- [ ] Están marcadas como sugerencias ("considera", "evalúa"), no como instrucciones
- [ ] Si no hay sugerencias relevantes, la sección no existe (no se rellena por rellenar)

**Longitud total**
- [ ] El PRD completo tiene menos de 500 palabras
- [ ] Si tiene más: ¿hay dos features mezcladas? ¿hay implementación en lugar de comportamiento?

---

## Checklist de los issues

**Cada issue tiene:**
- [ ] Referencia al PRD padre (número de issue o enlace)
- [ ] Descripción de comportamiento, no de implementación
- [ ] Criterios de aceptación específicos del issue (subconjunto del PRD o más específicos)
- [ ] Assumptions relevantes para este issue concreto
- [ ] Blocking relationships documentadas (qué lo bloquea, qué bloquea)
- [ ] Instrucción de cierre: "Cuando termines, comenta con un resumen de decisiones y cierra el issue"

**El tablero tiene:**
- [ ] El tracer bullet (lo más incierto) identificado y primero en la cola
- [ ] Issues ordenados según blocking relationships
- [ ] Issues que pueden ejecutarse en paralelo identificados

---

## Checklist de la constitution

- [ ] Technology Standards: todas las tecnologías activas del proyecto están listadas
- [ ] Security Requirements: las restricciones de seguridad no negociables están explícitas
- [ ] Performance & Scalability: hay al menos un requisito de rendimiento con número concreto
- [ ] Coding Standards: las convenciones más importantes están capturadas
- [ ] Compliance & Governance: si hay usuarios reales, los requisitos legales están aquí

**Validación:**
- [ ] El agente puede generar una spec sin contradecir la constitution
- [ ] Si el agente propone algo que viola la constitution, es detectado antes de ejecutar

---

## Checklist pre-QA

Antes de ejecutar el plan de QA, verifica:

- [ ] Todos los issues del tablero están cerrados con comentario de resumen
- [ ] El código producido ha sido leído (no auditado — leído) por al menos una persona
- [ ] Los criterios de aceptación del PRD están todos contemplados en al menos un issue
- [ ] Las decisions técnicas inesperadas del agente han sido revisadas y aceptadas

---

## Checklist post-QA

- [ ] Todos los criterios de aceptación del PRD pasan
- [ ] Los flujos de error funcionan como especificado
- [ ] Los casos límite identificados durante el grilling están verificados
- [ ] Lo que está en Out of Scope sigue sin estar implementado
- [ ] Los nuevos issues generados en QA están en el tablero para el siguiente ciclo

---

## La pregunta más importante

Antes de cualquier checklist, una sola pregunta:

**¿Si el agente leyera solo este documento, sabría qué tiene que ser verdad cuando termine, y sabría cuándo ha terminado?**

Si la respuesta es no — si hay ambigüedad sobre el comportamiento esperado o sobre los criterios de finalización — el documento no está listo.

No hay checklist que sustituya esa pregunta.

---

*Recurso del ebook [Spec-Driven Development](https://dominicode.com/spec-driven-development) — DominiCode*
