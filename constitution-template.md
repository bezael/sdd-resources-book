# Constitution — Template y ejemplo real

La constitution vive en `.specify/memory/constitution.md` si usas SpecKit.
Si no, puede vivir en cualquier lugar del repositorio — lo importante es que el agente la lea al inicio de cada sesión.

---

## El template

```markdown
# Constitution — [Nombre del proyecto]

## Technology Standards
[Las plataformas, frameworks, y stacks aprobados para el proyecto.
El agente no propone alternativas a estas tecnologías sin justificación explícita.]

- Backend: [runtime + versión]
- Frontend: [framework + librerías principales]
- Base de datos: [sistema + ORM si aplica]
- Auth: [sistema de autenticación]
- Deploy: [plataforma + entorno]
- Otros servicios: [email, pagos, storage, etc.]

---

## Security Requirements
[Restricciones de seguridad sin excepción. Si la constitution lo dice,
el agente no puede violarlo aunque sea más simple.]

- [Restricción de tokens / sesiones]
- [Restricción de datos sensibles / PII]
- [Restricción de secretos en código]
- [Otras restricciones de seguridad]

---

## Performance & Scalability
[Requisitos de rendimiento que el sistema tiene que cumplir.
El agente los tiene en cuenta al diseñar la arquitectura de cada feature.]

- [Tiempo de respuesta máximo en operaciones principales]
- [Usuarios concurrentes esperados]
- [Otras restricciones de rendimiento]

---

## Coding Standards
[Convenciones de código del proyecto.
Determinan la consistencia del código que produce el agente entre sesiones.]

- [Cobertura mínima de tests]
- [Convenciones de nombrado]
- [Restricciones de complejidad / tamaño de funciones]
- [Reglas del lenguaje: tipos, null safety, etc.]
- [Otras convenciones]

---

## Compliance & Governance
[Regulaciones, accesibilidad, auditoría.
Para proyectos personales puede ser mínimo. Para proyectos con usuarios reales, aquí van los requisitos legales.]

- [Accesibilidad]
- [Regulaciones de datos (RGPD, CCPA, etc.)]
- [Auditoría]
```

---

## Ejemplo real: proyecto web moderno

Este es un ejemplo de constitution para una aplicación web con Node.js, Next.js, y PostgreSQL. Adáptalo a tu stack.

```markdown
# Constitution — AI Spec Builder

## Technology Standards
- Backend: Node.js 20 o superior
- Frontend: Next.js 16 + React 19 + Tailwind CSS
- Base de datos: PostgreSQL via Prisma ORM
- Auth: Clerk — no implementar sistemas de auth propios
- Deploy: Vercel (frontend + API routes) — no Docker en producción
- Email: SendGrid para emails transaccionales
- IA: Anthropic SDK (Claude) — no OpenAI ni otros modelos sin aprobación

## Security Requirements
- Tokens de sesión exclusivamente en httpOnly cookies — nunca localStorage
- API keys exclusivamente en variables de entorno — nunca en código
- Nunca loguear PII (emails, nombres, IPs de usuarios)
- Validar y sanitizar todo input de usuario antes de pasarlo a la base de datos
- Las rutas de API que acceden a datos de usuario requieren autenticación Clerk

## Performance & Scalability
- Las páginas tienen que cargar en menos de 2 segundos en conexión 4G
- Los endpoints de API deben responder en menos de 500ms en el percentil 95
- Las queries a base de datos deben incluir índices para los campos de búsqueda
- El sistema tiene que soportar 500 usuarios concurrentes sin degradación

## Coding Standards
- TypeScript estricto — no usar `any`, siempre tipos explícitos
- Cobertura de tests mínima del 80% en lógica de negocio crítica
- Nombrado de variables y funciones en inglés
- Comentarios en español cuando el código no es autoexplicativo
- Funciones de más de 40 líneas requieren justificación o refactor
- No crear abstracciones para uso único — tres usos mínimo antes de abstraer
- Commits en inglés con formato convencional (feat:, fix:, chore:)

## Compliance & Governance
- WCAG 2.1 nivel AA para todos los componentes de interfaz
- Consentimiento explícito antes de recopilar cualquier dato de usuario
- Los usuarios pueden solicitar eliminación de sus datos — el sistema tiene que soportarlo
- Logs de auditoría para acciones sobre datos sensibles (crear, modificar, eliminar)
```

---

## Cómo escribir la constitution para un proyecto existente

Si el proyecto ya existe, no inventes restricciones nuevas. Documenta las que ya tienes implícitamente.

Pregúntale al agente:

*"Lee el código de este proyecto y genera un draft de la constitution capturando las decisiones técnicas que ya existen: qué tecnologías se usan, qué patrones se siguen, qué restricciones hay implícitas en el código actual."*

El agente produce un draft. Tú lo revisas, corriges lo que está mal, y añades lo que falta.

No va a ser perfecto en el primer intento. Va mejorando con cada iteración.

---

## Lo que NO va en la constitution

La constitution captura principios. No procedimientos.

**No va:**
- Instrucciones sobre cómo comportarse el agente (eso va en CLAUDE.md)
- Decisiones específicas de features (eso va en las specs)
- Código de ejemplo de cómo implementar algo
- Preferencias personales que no son restricciones reales del proyecto

**Sí va:**
- Cualquier cosa que, si se viola, hace que el resultado sea incorrecto independientemente de la calidad de la implementación

---

*Recurso del ebook [Spec-Driven Development](https://dominicode.com/spec-driven-development) — DominiCode*
