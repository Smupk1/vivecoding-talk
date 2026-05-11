# Speaker Notes — Vibe Coding Workshop (Español)

> Notas extendidas para el orador. Lo que decir, dónde pausar, qué preguntas hacer, dónde podés perder a la audiencia.

**Audiencia**: estudiantes de CS de años superiores. Ya programan. Saben qué es una API, una base de datos, una request HTTP. No insultes su inteligencia explicando lo básico — pero tampoco asumas que ya pensaron en arquitectura.

**Duración total**: 90 minutos. Llevá un cronómetro discreto.

---

## Bloque 1: ¿Qué es vibe coding? (min 5-15, 10 min)

### Lo que decir

> "Antes de tirar código, pongámonos de acuerdo en qué estamos hablando.
>
> En febrero de 2025, Andrej Karpathy — uno de los creadores de OpenAI, después en Tesla — tuiteó un término: **vibe coding**.
>
> Su definición original era casi una broma: 'te entregás a la vibra, te olvidás de que el código existe'. Pero el término se viralizó y se distorsionó.
>
> Hoy lo usan dos campos opuestos:
> - Los **fans**: 'es el futuro, no necesitamos saber programar'
> - Los **críticos**: 'es una receta para el desastre'
>
> Yo creo que **los dos están equivocados**, y por eso esta charla."

### Pausa y pregunta

> "Levantá la mano si alguna vez usaste GitHub Copilot, Cursor, ChatGPT o Claude para escribir código que después comiteaste a producción."

(Espera 5 segundos. Vas a ver 80% de manos arriba.)

> "Buenísimo. La pregunta no es **si** lo usás. La pregunta es **cómo**."

### Lo que NO es vibe coding (slide)

Pasá rápido. Es obvio. Pero el punto es **anclar** que no estamos hablando de la versión naive.

### Lo que SÍ es vibe coding (slide)

Detenete acá. Especialmente en el tercer punto:

> "**Multiplicador de criterio**. Esa palabra es clave. Si tu criterio es malo, el modelo te lo multiplica. Si tu criterio es bueno, también. La IA no es un nivelador — es un amplificador."

### Why now

Tres puntos rápidos. Si alguien pregunta por benchmarks, mencioná:
- GPT-4 (2023) podía escribir funciones aisladas
- Claude 3.5 / GPT-4o (2024) podían navegar codebases
- Claude 4.x / Sonnet 4.6+ (2025-2026) pueden ejecutar trabajo agentico de horas

**Trampa que ya viste**: alguien va a preguntar "¿pero entonces no van a reemplazar a los programadores?". Respuesta:

> "Van a reemplazar a los programadores que **no usen** IA. No a los que la usen bien. Es la misma historia que con cualquier herramienta que multiplica productividad — calculadoras, IDEs, internet. El trabajo se mueve hacia arriba en la cadena de abstracción."

---

## Bloque 2: Las dos trampas mortales (min 15-25, 10 min)

### Trampa 1: Sin fundamentos

**Acá tenés que ponerle fuerza.** Es el punto central de la charla. No te aceleres.

> "Hay una analogía que uso siempre: imagínense que les regalan una excavadora industrial. Sin haber manejado nunca ni un auto.
>
> ¿Pueden 'usarla'? Sí. Pueden encenderla, mover una palanca, hacer un movimiento.
>
> ¿Saben **lo que están haciendo**? No. Y la primera vez que algo salga mal — y va a salir mal — no van a saber ni por dónde empezar.
>
> Eso es vibe coding sin fundamentos."

### Pausa y mostrá el slide "El modelo no te enseña"

> "Esto es contraintuitivo. La gente cree que como el modelo 'te explica', te enseña.
>
> No te enseña. Te **da la respuesta**. Y darte la respuesta es la forma más rápida de **no aprender**.
>
> Pensá: ¿cuántas veces, en clase, el profe les dijo 'no les voy a dar la fórmula, intenten derivarla'? Esa fricción es donde se aprende.
>
> El modelo elimina toda esa fricción. Por eso es peligroso si no la reinstalás vos a propósito."

### Trampa 2: Creer que el modelo "sabe"

> "El modelo es un predictor estadístico. Eso suena despectivo, pero no lo es. Es una descripción técnica.
>
> Lo que significa: el modelo predice **el próximo token más probable** dado el contexto. Y a veces, lo más probable **no es lo correcto**.
>
> Ejemplo real: pídanle a cualquier modelo que use una API que cambió entre versiones. Va a usar la versión vieja, porque era 'lo más común' en sus datos de entrenamiento.
>
> ¿La solución? Leer su output. Cuestionarlo. Pasarle docs actualizadas. **Dirigirlo**."

### Discusión de 3 minutos

Esto es clave. **Hacé que hablen entre ellos primero** (2 min), después escuchá 2-3 ejemplos al aire.

Si nadie habla, tirá vos un ejemplo personal: una vez Claude me inventó una función de `crypto.subtle` que no existe. Compiló porque TS no lo agarró. Rompió en runtime.

---

## Bloque 3: Hands-on 1 — Astro Portfolio (min 25-40, 15 min)

### Antes de empezar

**Pediles que ya hayan corrido `pnpm install` antes** (está en `setup.md`). Si no lo hicieron, los 5 min iniciales se vuelven 12.

### Tu plan en vivo

1. **Min 0-2**: Vos abrís el repo, corrés `pnpm dev`, mostrás el sitio.
2. **Min 2-7**: Recorrido por la estructura. `src/pages/`, `src/components/`. Detenete en `index.astro` y mostrá que **no es JSX, es HTML real con frontmatter**.
3. **Min 7-10**: El ejercicio del cambio de paleta. Que abran `global.css`, cambien los colores, vean el hot-reload.
4. **Min 10-15**: Discusión Astro vs Next.

### Lo que NO hagas

- No expliques qué es Vite. Pierden 5 min y no es el punto.
- No expliques las CSS variables si nadie pregunta. Asumí que las conocen.
- No te metas en SSR/SSG/ISR. Es otro rabbit hole.

### Punto pedagógico fuerte para upper-year

> "Astro hace algo que React/Next no hacen por default: **te obliga a justificar el JavaScript que mandás al cliente**.
>
> En React, todo es un componente, todo se hidrata, todo viaja al cliente. Es opt-out: hay que **pedir explícitamente** que algo sea estático (RSC).
>
> En Astro es al revés: todo es estático, hay que **pedir explícitamente** que algo se hidrate (`client:load`, `client:idle`, `client:visible`).
>
> Esa inversión de default es **diseño**. Cambia qué decisiones tomás sin pensar."

---

## Bloque 4: Hands-on 2 — Biblioteca CRUD (min 40-65, 25 min)

### Este es el bloque más largo. Cuidá el tiempo.

### Tu plan en vivo

1. **Min 0-3**: Setup. Que cada uno corra:
   ```bash
   pnpm db:migrate:local
   pnpm db:seed:local
   pnpm dev
   ```
2. **Min 3-5**: Tour rápido por la UI. Registrar, login, crear libro.
3. **Min 5-15**: Tour por el código. **No leas todo. Mostrá las piezas clave**:
   - `wrangler.toml` — el binding declarativo de D1 y DO
   - `src/index.ts` — Hono routes, mostrá un endpoint público y uno con auth
   - `src/session-store.ts` — el Durable Object completo (es chico, léelo entero)
   - `src/auth.ts` — explicá PBKDF2 brevemente
4. **Min 15-25**: La discusión del DO. Slide "alternativas para sesiones". Aquí es donde brilla la charla.

### Cuando lleguen al DO

**Pausá largo aquí.** Es el concepto más nuevo. Probablemente nunca usaron algo así.

> "Pregunta para ustedes: en cualquier app que hayan construido — ¿dónde guardan las sesiones?
>
> [Esperá respuestas: 'en una tabla', 'en Redis', 'en JWT'.]
>
> OK. ¿Y por qué cada una de esas tiene **problemas**?"

Guialos a:
- Tabla SQL → latencia, carga en la DB
- Redis → otro servicio que mantener, single point of failure
- JWT → no se puede revocar sin blacklist

> "El Durable Object es **una primitiva nueva**: te da estado consistente serverless. No tenés que mantener Redis. No tenés que hacer queries a Postgres. Y es transaccional por diseño.
>
> Esto **no existía** hace 3 años. Es genuinamente nuevo."

### Modelo de consistencia

Si hay tiempo, profundizá:

> "Single-threaded por instancia significa que dentro de un DO, **no hay race conditions**. Si dos requests llegan a la misma sesión, se procesan en orden.
>
> Comparen con Postgres: `BEGIN; SELECT ... FOR UPDATE; UPDATE ...; COMMIT;` — toda esa danza es para emular lo que el DO te da gratis."

### Si sobra tiempo (raro)

Mostrá `/api/stats` y cómo el DO mantiene un conteo de sesiones activas que sobrevive a cold starts. Eso es **estado vivo distribuido**.

---

## Bloque 5: Vibe coding en acción (min 65-80, 15 min)

### Este bloque es donde la charla cierra el círculo

Las dos primeras horas fueron "acá tienen herramientas y conceptos". Este bloque es "ahora veamos cómo se construye con IA **bien**".

### Mal prompt vs buen prompt

Detenete en cada fila de la tabla. **No la leas — comentala**.

> "Miren la última fila. 'Mostrame el plan antes de tocar código'. Esa frase cambia toda la dinámica.
>
> Sin esa frase, el modelo te tira 200 líneas de código. Vos las copiás. Tal vez funcionan, tal vez no.
>
> Con esa frase, el modelo te dice **qué va a hacer** primero. Vos lo revisás. Lo cuestionás. Y recién después le pedís el código.
>
> Esa pausa es **donde vivís vos**. Es donde dirigís."

### Live exercise

**Sé claro con las reglas**:

1. Plan antes de código.
2. Cuestionar al menos UNA decisión.
3. Explicar al compañero.

Caminá entre los bancos. Mirá pantallas. Cuando alguien tenga un prompt mediocre, sentate al lado y mejoralo con él.

**Lo más importante**: cuando alguien acepte código sin leerlo, paralo:

> "Pará. ¿Qué hace esa línea?"

Si no puede responder, dejalo pensar 30 segundos. Después decile que vuelva al modelo y pida que se la explique. Que **lo investigue**.

---

## Bloque 6: Cuándo NO (min 80-90, 10 min)

### Esto es el cierre honesto

Es donde la mayoría de las charlas tipo "AI is the future!!!" fallan. Vos no falles.

> "Si la única lección que se llevan de hoy es que **la IA es genial, úsenla siempre** — fallé.
>
> Hay zonas donde vibe coding es la elección **incorrecta**. Y reconocerlas es lo que separa a alguien que sabe usar IA de alguien que se cree que sabe."

Recorré las cinco zonas. Detenete especialmente en la #4:

> "**Código que vos no podrías escribir.** Esta es la regla de oro. Si te entregaron un sistema y no entendés cómo funciona, no estás programando — estás **manteniendo un misterio**. Y los misterios se vuelven crisis."

### La pregunta de los $10,000

Léela despacio.

> "Si esto se rompe a las 3am, ¿podés debuggearlo?
>
> Si la respuesta es no — no es tu código. Es código que vive en tu repo. Hay una diferencia.
>
> En tu primer trabajo, vas a estar de guardia. Te van a llamar a las 3am. El sistema va a estar tirado. Y la única persona que puede arreglarlo sos vos.
>
> En ese momento, no podés pedirle a Claude que te explique el código que vos mismo escribiste hace 3 meses. **Ese conocimiento lo tenés vos, o no existe.**"

### Cierre

Slide final, 5 puntos clave. Léelos despacio. Después:

> "Los repos están públicos. Los van a usar para el TP. Si alguien arma algo genial encima, me lo mostrás.
>
> Preguntas?"

---

## Q&A — preguntas probables y cómo responder

**P: ¿Cuál es mejor, Claude o ChatGPT?**

> Depende del trabajo. Claude es mejor en código largo y refactors. ChatGPT/GPT es mejor en exploración rápida. Yo uso los dos.

**P: ¿No vamos a quedar sin trabajo?**

> Los que no usen IA, sí. Los que la usen como multiplicador, no. El trabajo va a moverse de 'escribir código' a 'diseñar sistemas' y 'verificar IA'. Más interesante, no menos.

**P: ¿Vale la pena aprender React si la IA lo hace por mí?**

> Sí. Sin entender React no vas a poder **dirigir** al modelo cuando escriba React. Vas a publicar código sin saber qué publica.

**P: ¿Cuánto cuesta esto en producción?**

> El stack que mostré (Cloudflare free tier) aguanta una app real con hasta ~100k requests/día sin costo. Si tu app crece más, hablamos de $5-20/mes. Mucho más barato que un VPS.

**P: ¿Cómo aprendo los fundamentos si la IA me da las respuestas?**

> Forzate a no usarla cuando estés aprendiendo algo nuevo. Usala cuando ya sabés lo que querés. Es disciplina, no técnica.
