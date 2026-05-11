# Speaker Notes — Vivecoding Workshop (Español)

> Guion ampliado. Qué decir, dónde pausar, qué preguntar, dónde puedes perder a la audiencia.

**Audiencia**: estudiantes universitarios de CS, años superiores. Ya programan. Saben qué es una API, una base de datos, una request HTTP.

**Duración**: 90 minutos. Lleva un cronómetro.

**Tono**: directo, primera persona, sin adornos. Cuenta historias específicas. Cuando algo no lo sepas, dilo.

---

## Setup (min 0-5)

Pide que cada uno corra:

```bash
cd ~/workshop/astro-portfolio-demo && pnpm dev
```

Mientras verifica que arranque, abre tú la primera slide.

Si alguien llega sin haber corrido `setup.md`, **no lo esperes**. Que arranque mientras tú avanzas.

---

## Cold Open: "Did you vibe code it?" (min 5-10)

### Qué decir

Cuenta la historia tal cual está en el manifiesto. No la dramatices, no la adornes — es buena por sí sola.

> "Cuando entré a IT Audit Labs, mi jefe me preguntó: *¿Lo vibe codeaste?*. Yo no sabía qué significaba. Sentí vergüenza. Lo googleé esa noche.
>
> Semanas después, me corrigió: *Es vibe coding, no vive coding.*
>
> Tenía razón en que lo decía mal. Estaba equivocado en que era un error."

Pausa larga aquí. Deja que la frase aterrice.

### Por qué importa

Esta no es una charla sobre semántica. Es una charla sobre **disciplina**. La historia del whiteboard te da licencia para hablar del tema sin sonar como un evangelista de IA más.

---

## Acto I: Vibecoding vs Vivecoding (min 10-20)

### El cuadro

Cuando muestres la tabla, **no la leas**. Coméntala fila por fila:

> "Philosophy. El vibecoder tira un d20 y reza. El vivecoder trata a la IA como el junior más poderoso que ha manejado.
>
> Specs. El vibecoder no las escribe. El vivecoder las escribe *antes* del código. Si no puedes escribir el spec, no entiendes el cambio. Punto."

Sigue así. Tres filas son suficientes — no recorras las siete o pierdes la atención.

### El cierre del cuadro

> "Misma herramienta. Mismos modelos. Disciplina distinta. **Esa es la charla completa.** El resto son 80 minutos de evidencia."

### Discusión rápida (3 min)

> "Levanten la mano si han usado Copilot, Cursor, ChatGPT o Claude para escribir código que después comitearon a producción."

Espera. Vas a ver 80% de manos arriba.

> "Bien. La pregunta no es *si* lo usan. La pregunta es **cómo**."

### Why now

Tres puntos rápidos. Si alguien pregunta benchmarks específicos:

- GPT-4 (2023) — funciones aisladas
- Claude 3.5 / GPT-4o (2024) — navegan codebases
- Claude 4.x (2025-2026) — trabajo agéntico de horas

**Trampa que vas a ver**: alguien va a preguntar *"¿no van a reemplazarnos?"*. Respuesta:

> "Van a reemplazar a los que no usen IA. No a los que la usen bien. Es la misma historia con cualquier herramienta que multiplica productividad. El trabajo se mueve hacia arriba en la cadena de abstracción."

---

## Acto II: El stack (min 20-25)

### Multi-modelo

Esta slide tiene cinco filas. **Comenta cada una en una línea**:

- **Gemini**: planning. Contexto largo, buen output estructurado.
- **Claude**: building. El código que va a producción.
- **Workers AI**: edge fallback. Barato. Rápido. Bueno para iteración.
- **Codex**: hunting. Pasada adversarial sobre los diffs.
- **CodeRabbit + Copilot**: review automático. Dos opinions sobre cada merge.

### El punto clave

> "Cada uno se equivoca a veces. La única forma de descubrirlo es que otro disienta."

Esa frase es el corazón. **Pausala.**

### Los agentes de soporte

Tres slides. Una por agente. **No los expliques en detalle** — los estudiantes no necesitan saber cómo funciona Engram internamente. Dilo así:

> "Engram es memoria persistente — un RAG. Lo importante no es el RAG. Lo importante es que **nada vive solo en el historial de chat**."
>
> "Gentle es grounding — el agente que me aterriza. La semana pasada, 10 de la noche, un stakeholder me pidió reescribir un producto. Gentle dijo: *no, no esta noche.* Y tenía razón."
>
> "Warlock es seguridad — auditoría. Detectó dos CVEs reales en 48 horas. A esos vamos a llegar."

---

## Pipeline SDD (min 25-30)

### El DAG

Cuando muestres el diagrama, di esto:

> "Spec y design alimentan tasks **en paralelo**. Verify es un gate, no una vibra. Archive sincroniza y cierra.
>
> Este es el mismo SDLC que ven en la universidad. **La diferencia es que ahora es ejecutable.** Cada flecha es un comando."

### Por qué funciona a escala

> "Ningún agente, y ningún humano, tiene que sostener el proyecto entero en la cabeza. El DAG lo sostiene.
>
> Es la diferencia entre 'estoy haciendo malabares con cinco bolas' y 'tengo un sistema que sabe dónde está cada bola'."

---

## Práctica I: Astro Portfolio (min 30-45)

### Antes de empezar

Que **ya** hayan corrido `pnpm install` antes (está en `setup.md`). Si no, los primeros 5 min se vuelven 12.

### Tu plan en vivo

1. **Min 0-2**: tú abres el repo, corres `pnpm dev`, muestras el sitio.
2. **Min 2-7**: tour por la estructura. `src/pages/`, `src/components/`. Detente en `index.astro` y muestra que **no es JSX — es HTML real con frontmatter**.
3. **Min 7-12**: ejercicio del cambio de paleta. Que abran `global.css`, cambien los colores, miren el hot-reload.
4. **Min 12-15**: la slide de Astro vs Next.

### Qué NO hacer

- **No expliques qué es Vite.** Pierdes 5 min, no es el punto.
- **No expliques CSS variables** si no preguntan. Asume que las saben.
- **No te metas en SSR/SSG/ISR** — otro rabbit hole.

### El concepto pedagógico

> "Astro **invierte el default** de React. En React todo es JS hasta que pides estático. En Astro todo es estático hasta que pides hidratación.
>
> Esa inversión no es performance. **Es diseño.** Cambia qué decisiones tomas sin pensar. Y las decisiones que tomas sin pensar son las que definen tu arquitectura a largo plazo."

---

## Práctica II: Biblioteca (min 45-70)

### El bloque más largo. Cuida el tiempo.

### Tu plan en vivo

1. **Min 0-3**: setup. Todos corren:
   ```bash
   pnpm db:migrate:local
   pnpm db:seed:local
   pnpm dev
   ```
2. **Min 3-6**: tour por la UI. Registrar, login, crear libro.
3. **Min 6-15**: tour por el código. **No leas todo. Muestra las piezas clave**:
   - `wrangler.toml` — el binding declarativo de D1 y DO
   - `src/index.ts` — Hono routes, muestra un endpoint público y uno con auth
   - `src/session-store.ts` — el Durable Object completo (es chico, léelo entero)
   - `src/auth.ts` — explica PBKDF2 en 30 segundos
4. **Min 15-25**: la discusión del DO. Esto es lo más importante del workshop.

### Cuando lleguen al DO

**Pausa larga aquí.** Es el concepto más nuevo. Probablemente nunca usaron algo así.

> "Pregunta para ustedes: en cualquier app que hayan construido — ¿dónde guardan las sesiones?
>
> [Espera respuestas: 'en una tabla', 'en Redis', 'en JWT'.]
>
> OK. ¿Y por qué cada una de esas tiene **problemas**?"

Guíalos a:
- SQL → latencia, carga en la DB
- Redis → otro servicio que mantener, single point of failure
- JWT → no se puede revocar sin blacklist

> "El Durable Object es **una primitiva nueva**: te da estado consistente serverless.
>
> Esto no existía hace 3 años. Es genuinamente nuevo. Y resuelve un problema que en otros stacks resuelves apilando Redis + Postgres + lógica custom."

### La regla que generaliza

Esta slide es clave para tu identidad como security engineer:

> "Cada AI tool es un endpoint autenticado.
>
> Si no expondrían la operación como un REST call sin guardias, no pueden exponerla como un tool sin guardias.
>
> El schema de Zod no es un boundary de seguridad. **El handler sí.**"

Pausa larga. **Esto es lo que aprendiste en producción**, no en un libro. Diles que es lo que aprendiste con la CVE #2.

---

## Casos de estudio: las dos CVEs (min 70-78)

### Cómo contarlas

No las dramatices. Cuéntalas como las cuentas en el manifesto — directas, específicas, con la lección al final.

### CVE #1

> "Había una función llamada `requireOrgAdmin()`. Cualquier miembro de una organización era tratado como admin automáticamente, sin importar su rol.
>
> Parecía intencional. El patrón era viejo. Nadie lo cuestionaba.
>
> El agente de seguridad corrió una auditoría sin que se lo pidiera. Encadenó con code-review. Confirmó: bug real de privilege escalation.
>
> **Habría vivido en producción durante meses.**
>
> Lección: **lo que parece un feature, a veces es un CVE.** Código viejo no es código seguro. Código viejo es código sin auditar con un historial más largo."

### CVE #2

> "El asistente de IA tenía un tool llamado `get_ticket_detail`. Tomaba cualquier ticket por ID usando una cuenta de servicio. Sin chequeo de ownership.
>
> Un usuario en organización A podía pedir un ticket de organización B. Y el asistente lo entregaba.
>
> Caught durante la auditoría de seguridad del rework, **antes de producción**.
>
> Lección que generaliza: **cada AI tool es un endpoint autenticado.** Esa frase es la única que necesitan recordar del bloque de seguridad."

---

## Las cinco scars (min 78-82)

### Por qué este bloque

Muchas charlas de IA solo muestran wins. **Tú muestras scars.** Esa honestidad es tu credibilidad.

Léelas rápido. Una por una. **Sin disculparte por ninguna.**

### El cierre del bloque

> "El workflow es bueno. No es magia. El feedback del usuario sigue siendo irreemplazable.
>
> Si después de hoy creen que el SDD los va a salvar de todo, fallé. **Los va a salvar del 80%.** El 20% lo sigues haciendo tú."

---

## Las 5 reglas (min 82-87)

### Cómo presentar

Cinco slides. Una regla cada una. **Pausa larga después de leer cada regla.**

Las reglas son tu firma — tu manifiesto. Léelas con peso.

> **Regla 01 — Specs antes del código. Siempre.**
>
> Si no puedes escribir el spec, no entiendes el cambio. Deja de tipear prompts.

> **Regla 02 — Un solo modelo nunca es la respuesta.**
>
> Cada modelo tiene una fortaleza. La mezcla es el moat.

> **Regla 03 — Design is code. Merge it.**
>
> Las decisiones de arquitectura viven en version control. No en Notion.

> **Regla 04 — "Compila" ≠ "funciona".**
>
> Verify es una fase, no una vibra.

> **Regla 05 — La IA es tu junior, no tu genius.**
>
> No mergees el PR de un junior sin leerlo.

---

## El número + cierre (min 87-90)

### El número

> "De baseline a vivecoding: **6 meses a 1 mes**.
>
> Producción. Multi-tenant. 78 tests pasando. Dos auditorías de seguridad.
>
> La velocidad **no vino de saltarse pasos**. Vino de paralelizar los pasos correctos con los modelos correctos."

### Cierre

> "Tres cosas para llevarse a casa.
>
> Uno: **disciplina le gana a vibras.**
>
> Dos: **el modelo correcto para el trabajo correcto.**
>
> Tres: **la IA es un amplificador.** No reemplaza al ingeniero. Hace al entrenado seis veces más rápido."

Pausa. Última slide:

> "Vibecoding es roleplay. **Vivecoding es una campaña con disciplina.**
>
> Los repos están públicos. El manifiesto completo está en vivecoding.dev.
>
> Preguntas?"

---

## Q&A — preguntas probables

**P: ¿Cuál modelo es mejor, Claude o ChatGPT?**

> Depende del trabajo. Claude es mejor en código largo y refactors. GPT es mejor en exploración rápida y creatividad. Yo uso los dos. La pregunta correcta no es cuál es mejor — es *para qué*.

**P: ¿No nos van a reemplazar?**

> A los que no usen IA, sí. A los que la usen bien, no. El trabajo va a moverse de 'escribir código' a 'diseñar sistemas y verificar IA'. Más interesante, no menos.

**P: ¿Vale la pena aprender React si la IA lo escribe por mí?**

> Sí. Sin entender React no vas a poder **dirigir** al modelo cuando escriba React. Vas a estar publicando código sin saber qué publicas. Y cuando se rompa, no vas a poder arreglarlo.

**P: ¿Cuánto cuesta esto en producción?**

> El stack que mostré (Cloudflare free tier) aguanta hasta 100k requests/día sin costo. Si tu app crece, hablamos de 5-20 USD/mes. Más barato que un VPS.

**P: ¿Cómo aprendo los fundamentos si la IA me da las respuestas?**

> Disciplina, no técnica. Cuando estés aprendiendo algo nuevo, no la uses. Cuando ya sepas lo que quieres, úsala. La diferencia es: ¿estoy aprendiendo, o estoy ejecutando?

**P: ¿Por qué Cloudflare y no AWS?**

> Por el plan gratuito y por el modelo de edge. AWS gratuito te dura un año y después te empieza a cobrar. Cloudflare gratuito **es permanente** dentro de los límites. Para aprender y para apps pequeñas-medianas, no hay competencia.

**P: ¿Qué pasa si un día Cloudflare cierra?**

> Misma respuesta que para cualquier vendor: portabilidad. Hono corre en Workers, Bun, Node, Deno. Astro genera HTML estático que sirve cualquier servidor. D1 es SQLite — los datos salen como `.sqlite`. La arquitectura que mostré es portable.
