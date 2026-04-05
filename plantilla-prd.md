# Plantilla PRD completa

Copia esto. Rellénalo. Borra las instrucciones en cursiva cuando hayas completado cada sección.

Target: menos de 500 palabras para una feature de tamaño medio.

---

```markdown
# PRD: [Nombre de la feature]
> Issue #N | Fecha: YYYY-MM-DD | Estado: draft / aprobado

## Problem Statement
[1-2 frases. Qué está roto o qué falta. Por qué importa ahora.
No es la solución. Es el problema.]

Ejemplo:
"El módulo de auth guarda session tokens en localStorage. Legal lo flaggeó
como riesgo de compliance. Hay que migrar a httpOnly cookies antes del Q2."

---

## Solution
[El destino, no el camino. Qué tiene que ser verdad cuando el trabajo
esté hecho, desde el punto de vista del usuario o del sistema.
Sin mencionar tecnologías ni implementación.]

Ejemplo:
"Los usuarios podrán autenticarse. Las sesiones persistirán entre recargas.
Un logout invalida la sesión en servidor y cliente. Los tokens nunca tocan
el JavaScript del frontend."

---

## User Stories
[3-4 historias máximo. Formato: Como [rol], cuando [acción], entonces [resultado].
Si necesitas más de 6, probablemente tienes dos features mezcladas.]

Como [rol],
cuando [acción],
entonces [resultado esperado].

Como [rol],
cuando [acción],
entonces [resultado esperado].

---

## Constraints
[Restricciones no negociables. Si se violan, el resultado es inválido
independientemente de lo demás. Si no tienes restricciones reales, deja vacío.]

- [Restricción concreta]
- [Restricción concreta]

---

## Acceptance Criteria
[Cada criterio debe poder pasar o fallar. Si no puede fallar, no es un criterio.
Formato: acción → resultado observable.]

- [ ] [Input / condición] → [output / comportamiento esperado]
- [ ] [Input / condición] → [output / comportamiento esperado]
- [ ] [Input / condición] → [output / comportamiento esperado]

---

## Out of Scope
[Lo que explícitamente NO entra en este PRD. Mínimo 3 entradas.
Sin esto, el agente implementa todo lo relacionado.]

- [Feature relacionada que no entra] — [cuándo / dónde va]
- [Feature relacionada que no entra] — [cuándo / dónde va]
- [Feature relacionada que no entra] — [cuándo / dónde va]

---

## Assumptions ⚠️
[La sección más crítica. Qué asumes sobre el estado actual del sistema.
Si una assumption está mal, todo el downstream está mal.]

- [Estado actual de la parte del sistema que vamos a tocar]
- [Tecnologías o librerías que ya existen]
- [Esquemas de base de datos relevantes]
- [Presencia o ausencia de tests]

---

## Implementation Notes
[Opcional. Sugerencias, no instrucciones. El agente puede ignorarlas
si tiene mejor razón. Usa "considera" en lugar de "usa".]

- Considera [opción A] vs [opción B] según [criterio]
```

---

## Checklist rápido antes de aprobar

- [ ] ¿Tiene menos de 500 palabras?
- [ ] ¿La sección Solution describe comportamiento, no implementación?
- [ ] ¿Los Acceptance Criteria pueden pasar o fallar?
- [ ] ¿El Out of Scope tiene al menos 3 entradas?
- [ ] ¿Las Assumptions reflejan el estado real del sistema?
- [ ] ¿Las Implementation Notes están marcadas como sugerencias?

---

## Notas de uso

**Problem Statement vs Solution**
El Problem Statement describe el presente. La Solution describe el futuro. Si tu Solution menciona por qué existe el problema, está en la sección equivocada.

**Constraints vs Acceptance Criteria**
Los Constraints son las reglas del juego — lo que no puede violarse bajo ninguna circunstancia. Los Acceptance Criteria son la verificación — cómo sabes que el trabajo está hecho. No son lo mismo.

**El grilling antes de escribir**
Antes de completar este template, pídele al agente que te haga preguntas:
*"Voy a construir [X]. Antes de escribir el PRD, hazme todas las preguntas que necesites para entender el comportamiento esperado. Mínimo 10 preguntas."*
Responde las preguntas y después completa el template. La calidad del PRD mejora notablemente.

**Dónde guardar el PRD**
GitHub Issues: un issue por PRD, título `[PRD] Nombre de la feature`.
SpecKit: `specs/nombre-feature/spec.md`.
openSpec: donde tenga sentido para tu proyecto, de forma consistente.

---

*Recurso del ebook [Spec-Driven Development](https://dominicode.com/spec-driven-development) — DominiCode*
