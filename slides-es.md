---
marp: true
theme: default
paginate: true
backgroundColor: "#0f172a"
color: "#e2e8f0"
style: |
  section { font-family: 'Inter', system-ui, sans-serif; padding: 60px; }
  h1 { color: #38bdf8; font-weight: 800; }
  h2 { color: #38bdf8; border-bottom: 2px solid #334155; padding-bottom: 8px; }
  code { background: #1e293b; padding: 2px 8px; border-radius: 4px; color: #fde68a; }
  pre { background: #1e293b !important; border-radius: 8px; padding: 16px; }
  blockquote { border-left: 4px solid #38bdf8; padding-left: 16px; color: #94a3b8; font-style: italic; }
  strong { color: #fde68a; }
  em { color: #f472b6; }
  table { font-size: 22px; }
  .center { text-align: center; }
  .small { font-size: 22px; }
  .danger { color: #f87171; }
  .ok { color: #4ade80; }
---

<!-- _class: center -->

# Vibe Coding

## No es "copiar de ChatGPT"
## Es **dirigir modelos** para construir software real

<br>

**Workshop · 90 min · Manos al teclado**

---

<!-- _class: center -->

## Quién soy

**[Tu nombre]** — Senior Architect, 15+ años construyendo software

GDE · MVP · profe ocasional

Hoy: 90 min, dos demos reales, una idea central

---

## Reglas del workshop

1. **Esto es práctica, no exhibición.** Vas a clonar, romper y arreglar.
2. **Las preguntas no esperan.** Interrumpime.
3. **Si algo no me lo sé, lo digo.** Vos también podés.
4. **No copies sin entender.** Ese es el punto de toda la charla.

---

# Bloque 1
## ¿Qué es vibe coding?

<br>

> _"There's a new kind of coding I call vibe coding, where you fully give in to the vibes, embrace exponentials, and forget that the code even exists."_
>
> — Andrej Karpathy, Feb 2025

---

## Lo que NO es vibe coding

❌ Copiar y pegar de ChatGPT sin leer

❌ "El modelo escribe, yo aplaudo"

❌ Dejar de aprender porque "ya está la IA"

❌ Producir código que no podés mantener

---

## Lo que SÍ es vibe coding

✅ **Vos** decidís la arquitectura, el modelo ejecuta

✅ Iterar a velocidad 10× sobre **ideas que ya entendés**

✅ Usar al modelo como **multiplicador de tu criterio**, no como reemplazo

✅ **Push-back constante**: si el modelo está mal, lo discutís

---

## La pregunta honesta

<br>

# ¿Por qué AHORA?

<br>

Los LLMs cruzaron un umbral en 2024-2025:

- Contexto largo (1M tokens) → entienden tu codebase entero
- Tool use confiable → ejecutan tareas multi-paso
- Razonamiento sobre código → no solo autocompletan

**El costo de prototipar cayó ~10×. El costo de mantener no.**

---

# Bloque 2
## Las dos trampas mortales

---

## Trampa 1
### Vibe coding sin fundamentos

<br>

Querés construir una app con React.

No sabés qué es el DOM.

No sabés qué es un bundler.

No sabés qué es una request HTTP.

<br>

> _¿Cómo vas a **debuggear** algo que no entendés?_

---

## La verdad incómoda

<br>

# El modelo no te enseña

<br>

El modelo **acelera lo que ya sabés** y **oculta lo que no sabés**.

Si no entendés async/await, el código va a "funcionar" hasta que rompa en producción a las 3am.

**Los fundamentos no son opcionales. Son la diferencia entre dirigir y ser dirigido.**

---

## Trampa 2
### Creer que el modelo "sabe"

<br>

El modelo es un **predictor estadístico de texto**.

No "razona" como vos. No "verifica" su output.

Confunde APIs. Inventa funciones. Olvida tipos.

> _Si no leés su código, no estás programando — estás **publicando**._

---

## Discusión rápida (3 min)

<br>

¿Cuándo, en su experiencia, una IA les dio código que **parecía bien** pero estaba mal?

<br>

¿Cómo lo descubrieron?

---

# Bloque 3
## Hands-on 1: Portfolio con Astro

<br>

**Repo**: `Smupk1/astro-portfolio-demo`

```bash
cd ~/workshop/astro-portfolio-demo
pnpm dev
```

Abrir `localhost:4321`

---

## ¿Qué hay acá?

- **Astro 6** — generador de sitios estáticos basado en componentes
- **Cero React, cero Vue** — HTML + CSS + JS vanilla con `.astro`
- **Deploy a Cloudflare Workers** — global, gratis

<br>

**Conceptos pedagógicos** (para CS upper-year):

1. **Islands Architecture**: el sitio es HTML estático; solo "islas" hidratan JS donde lo necesitás. Comparalo mentalmente con SSR puro de Next.js.
2. **Zero JS by default** — el opuesto del SPA "everything is React".

---

## Experimento (5 min)

<br>

Abrí `src/styles/global.css`.

Cambiá la paleta a la de **tu universidad**.

<br>

Mientras lo hacés, **observá**: el hot-reload de Astro. La latencia. Lo poco que tarda.

¿Cuántas veces deployaste algo en producción para verificar un color cuando empezaste? 😅

---

## Por qué Astro y no Next.js

| Astro | Next.js |
|---|---|
| HTML por defecto, JS opcional | JS por defecto, HTML opcional |
| Ideal para sitios de contenido | Ideal para apps con mucho estado |
| Bundle inicial: ~0 kb JS | Bundle inicial: ~80-100 kb JS |
| Hidratación selectiva | Hidratación completa |

**Regla**: si tu sitio es 80% contenido y 20% interactividad → Astro. Si es al revés → React/Next.

---

# Bloque 4
## Hands-on 2: Biblioteca con Cloudflare Workers

<br>

**Repo**: `Smupk1/biblioteca-cloudflare-demo`

**Stack**: Workers + D1 + Durable Objects + Hono

Tres primitivas del free tier de Cloudflare en un solo proyecto.

---

## El plan gratuito de Cloudflare

| Servicio | Free tier |
|---|---|
| **Workers** | 100,000 requests/día |
| **D1** (SQL) | 5 GB · 25M reads/día · 50k writes/día |
| **Durable Objects** | 1M requests/mes · 400k GB·s |
| **R2** (storage) | 10 GB |
| **KV** | 100k reads/día |

<br>

**Conclusión**: una clase entera puede tirar carga contra esto sin que cueste un peso.

---

## Arquitectura

```
┌────────────┐    HTTPS    ┌────────────────────────────────┐
│  Browser   │────────────▶│  Worker (Hono router)          │
└────────────┘             │    /api/login, /api/books      │
                           └──────┬──────────────┬──────────┘
                                  ▼              ▼
                            ┌─────────┐    ┌──────────────┐
                            │   D1    │    │ Durable Obj  │
                            │ (SQL)   │    │  Sessions    │
                            └─────────┘    └──────────────┘
                            users,books    token→userId
```

---

## Setup en vivo (5 min)

```bash
cd ~/workshop/biblioteca-cloudflare-demo
pnpm db:migrate:local
pnpm db:seed:local
pnpm dev
```

Abrir `localhost:8787`

Registrarse · login · agregar libro · refresh stats

---

## ¿Por qué un Durable Object para sesiones?

<br>

# Esta es **la** pregunta de la charla

<br>

Discutámosla.

---

## Alternativas para guardar sesiones

| Opción | Problema |
|---|---|
| `Map` en memoria del Worker | Cada request puede caer en otro nodo. **No persiste.** |
| Cookie firmada (JWT) | Funciona pero **no se puede invalidar** sin blacklist |
| D1 (tabla `sessions`) | Funciona, pero cada validación = 1 query SQL |
| **Durable Object** | UNA instancia global, in-memory + persistente |

---

## El modelo mental clave

<br>

Los **Workers** son **stateless** por diseño — ejecutan y mueren.

Los **DOs** son **stateful** por diseño — viven, recuerdan, son consistentes.

<br>

> Cuando necesitás **un único punto consistente** en el mundo (sesiones, rate limiting, contadores, salas de chat) → DO.
>
> Para todo lo demás → Worker + D1.

---

## El modelo de consistencia de los DOs

<br>

**Single-threaded por instancia.** Si dos requests modifican la misma sesión, se serializan.

**Sin race conditions** dentro de un DO. Esto es enorme.

<br>

> Compará esto con tener que pensar en `SELECT ... FOR UPDATE` en Postgres.
>
> En un DO no existe el problema — es secuencial por diseño.

---

# Bloque 5
## Vibe coding en acción

<br>

## Vamos a agregar un feature **juntos**

<br>

**Feature**: marcar un libro como "prestado a X usuario"

Necesitamos: nueva columna en D1, endpoint nuevo, UI actualizada.

---

## Mal prompt vs buen prompt

<br>

❌ **Mal prompt**:
> "Agregale al CRUD que se pueda prestar un libro"

✅ **Buen prompt**:
> "En el repo de biblioteca, quiero agregar un sistema de préstamos.
> Schema: nueva tabla `loans` (id, book_id, user_id, taken_at, returned_at).
> Endpoint: `POST /api/books/:id/borrow` (auth required) que crea el loan
> y setea `disponible=0`. Si ya está prestado, devolver 409.
> Mostrame el plan antes de tocar código."

---

## Lo que cambia entre un prompt y el otro

| Mal prompt | Buen prompt |
|---|---|
| Le dejás todo al modelo | Vos decidís el shape |
| El modelo inventa el schema | Vos le pasás el schema |
| El modelo elige el status code | Vos elegís `409 Conflict` |
| El modelo te entrega código | Vos le pedís el **plan primero** |

**Quién dirige aquí?**

---

## Live exercise (10 min)

<br>

Cada uno, en su máquina, con su editor + IA:

**Pediles que agreguen el endpoint `POST /api/books/:id/borrow`**

Reglas:
1. Pedile al modelo el **plan antes del código**
2. Cuestionalo en al menos UNA decisión
3. Cuando el código compile, **explicale a tu compañero qué hace**

---

# Bloque 6
## ¿Cuándo NO vibe codeas?

---

## Las cinco zonas de peligro

1. **Código de seguridad crítico** (auth, crypto, payments) — leé cada línea
2. **Algoritmos con invariantes** — el modelo no "razona" sobre invariantes
3. **Migraciones de DB en prod** — un drop table mal y se acabó
4. **Código que VOS no podrías escribir** — si no lo entendés, no lo podés mantener
5. **Cuando el modelo se cae a "lo más común"** — APIs viejas, patrones desactualizados

---

## La pregunta de los $10,000

<br>

> _Si esto se rompe a las 3am, ¿podés debuggearlo?_

<br>

Si la respuesta es **no** → no es vibe coding, es **vibe shipping**.

Y vibe shipping te despide.

---

# Cierre

## Lo que se llevan de este workshop

1. **Vibe coding es una herramienta, no una identidad.** A veces sí, a veces no.
2. **Los fundamentos son innegociables.** Conceptos > código.
3. **El humano lidera.** Si el modelo dirige, perdiste.
4. **Push-back constante.** Si el modelo está mal, decíselo.
5. **Astro + Cloudflare Workers** = stack hermoso, gratis, y enseña conceptos modernos.

---

## Recursos

- 📚 [Astro Docs](https://docs.astro.build)
- ⚡ [Cloudflare Workers Docs](https://developers.cloudflare.com/workers/)
- 🔥 [Hono](https://hono.dev/)
- 🤖 [Claude Code](https://www.anthropic.com/claude-code)
- 🎯 [Cursor](https://cursor.sh/)
- 📖 Karpathy on vibe coding: [twitter.com/karpathy](https://twitter.com/karpathy)

<br>

**Repos del workshop:**
- `github.com/Smupk1/astro-portfolio-demo`
- `github.com/Smupk1/biblioteca-cloudflare-demo`

---

<!-- _class: center -->

# Gracias

## Preguntas?

<br>

Hablen entre ustedes también — la mejor forma de entender algo es explicárselo a otro.
