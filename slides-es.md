---
marp: true
theme: default
paginate: true
backgroundColor: "#0a0a0a"
color: "#e8e8e8"
style: |
  section { font-family: 'Inter', system-ui, sans-serif; padding: 60px; }
  h1 { color: #d4af37; font-weight: 800; letter-spacing: -0.02em; }
  h2 { color: #d4af37; border-bottom: 1px solid #2a2a2a; padding-bottom: 10px; font-weight: 700; }
  h3 { color: #8b9eff; }
  code { background: #1a1a1a; padding: 2px 8px; border-radius: 3px; color: #f4d03f; font-size: 0.85em; }
  pre { background: #111 !important; border: 1px solid #2a2a2a; border-radius: 6px; padding: 18px; font-size: 0.7em; }
  blockquote { border-left: 3px solid #d4af37; padding-left: 18px; color: #a0a0a0; font-style: italic; margin: 20px 0; }
  strong { color: #f4d03f; }
  em { color: #c084fc; }
  table { font-size: 22px; border-collapse: collapse; }
  th, td { padding: 8px 14px; border-bottom: 1px solid #2a2a2a; }
  th { color: #d4af37; text-align: left; }
  .center { text-align: center; }
  .small { font-size: 22px; }
  .mono { font-family: 'JetBrains Mono', monospace; }
  ul li { margin: 6px 0; }
---

<!-- _class: center -->

# Vivecoding

## Ingeniería asistida por IA como una **campaña**, no una tirada de dados

<br>

**Workshop · 90 min · Práctica en vivo**

<br>

<span class="mono" style="color:#666;font-size:14px">Samuel Cala · vivecoding.dev</span>

---

## Quién soy

**Samuel Cala** — Security Engineer en IT Audit Labs

SOC operations · SOAR automation · Security development

Hoy: 90 minutos. Dos proyectos reales. Una tesis.

<br>

> Vibecoding es roleplay. **Vivecoding es una campaña con disciplina.**

---

## Reglas del workshop

01. Esto es **práctica**, no exhibición. Vas a clonar, romper, y arreglar.
02. Las preguntas no esperan. Interrúmpeme.
03. Si no sé algo, lo digo. Tú también puedes.
04. **No copies lo que no entiendes.** Esa es la charla completa en una línea.

---

<!-- _class: center -->

# Cold Open

## *"Did you vibe code it?"*

---

## La historia

Cuando entré a IT Audit Labs, mi jefe me preguntó:

> *"¿Lo *vibe codeaste*?"*

Yo no sabía qué significaba. Lo googleé en mi casa esa noche. Sentí un poco de vergüenza por usar ChatGPT para escribir código.

Semanas después, mi jefe se paró frente al tablero y dijo:

> *"Estás pronunciándolo mal. Es **vibe** coding, no **vive** coding."*

Tenía razón en que lo decía mal.

**Estaba equivocado en que era un error.**

---

# Acto I
## Vibecoding vs Vivecoding

---

## La tesis, en un solo cuadro

| | **Vibecoding** | **Vivecoding** |
|---|---|---|
| **Filosofía** | Tira un d20. Reza. | Disciplina de ingeniería + IA como amplificador |
| **Specs** | Ninguna | Antes del código. Siempre. |
| **Pipeline** | Prompt → ship | explore → spec → design → apply → verify |
| **Modelos** | Uno, para todo | Multi-modelo con cross-check |
| **Tests** | Opcionales | TDD estricto. Authz invariants. |
| **Code review** | "Compila, entonces funciona" | En cada PR. Sin excepciones. |
| **Deuda técnica** | Crece más rápido de lo que escribes | El AI amplifica al ingeniero, no al revés |

**Misma herramienta. Mismos modelos. *Disciplina distinta.***

---

## El vibecoder

Tira un d20. Despacha lo que el modelo le entregue.

<br>

## El vivecoder

Trata a la IA como **el junior más poderoso que ha manejado**, y aplica el mismo rigor de ingeniería que aplicaría a cualquier otro contribuidor.

Porque la alternativa es **deuda técnica que compone más rápido de lo que puedes escribir código.**

---

## ¿Por qué importa ahora?

Los LLMs cruzaron un umbral entre 2024 y 2025:

- **Contexto largo** (1M+ tokens) → entienden codebases enteros
- **Tool use confiable** → ejecutan trabajo multi-paso
- **Razonamiento sobre código** → no solo autocompletan

<br>

**El costo de prototipar cayó ~10×.**
**El costo de mantener, no.**

Ese gap es donde vive vivecoding.

---

# Acto II
## El stack: agentes especializados

---

## Un solo modelo nunca es la respuesta

Cada modelo tiene una fortaleza. **La mezcla es la ventaja competitiva.**

| Modelo | Rol | Para qué |
|---|---|---|
| **Gemini** | Planner | Documentación, planning, SDDs, contexto largo |
| **Claude** | Builder | Implementación, refactor, código que despacha |
| **Cloudflare Workers AI** | Fallback | Llama/Kimi en el edge, iteración barata y rápida |
| **Codex** | Hunter | Bug bounty, error hunting, pasada adversarial sobre diffs |
| **CodeRabbit + Copilot** | Safety net | Dos reviewers, cada merge. Sin excepciones. |

El vibecoder elige uno y reza.

El vivecoder corre cinco — **porque cada uno se equivoca a veces, y la única forma de descubrirlo es que otro disienta.**

---

## Los agentes de soporte

**Engram** — Memoria persistente (RAG). Cada decisión, observación y CVE persiste. La próxima sesión sabe lo que aprendió la anterior. Nada importante vive solo en el historial de chat.

**Gentle** — Compañero de grounding. Te aterriza cuando estás espiralizando. *"No, eso no se hace hoy a las 10pm."*

**Warlock** — Auditor de seguridad. Detectó **dos CVEs reales en 48 horas** que la revisión humana no habría agarrado.

<br>

Cada uno hace su trabajo. Yo orquesto.

---

## El pipeline SDD (Spec-Driven Development)

```
/sdd-init     →  detectar stack & convenciones
   ↓
/sdd-explore  →  reconocer el terreno
   ↓
/sdd-propose  →  intent + scope + approach
   ↓
/sdd-spec     →  requirements + scenarios   ──┐
   ↓                                           ├→ /sdd-tasks → /sdd-apply → /sdd-verify → /sdd-archive
/sdd-design   →  decisiones de arquitectura ──┘
```

Spec y design alimentan tasks **en paralelo**. Verify es un gate, no una vibra. Archive sincroniza y cierra.

**El mismo SDLC que aprendiste en la universidad. Ahora ejecutable.**

---

## La razón por la que funciona a escala

Ningún agente — y ningún humano — tiene que sostener el proyecto entero en la cabeza.

**El DAG lo sostiene.**

Cada fase tiene preconditions claras, outputs claros, y un handoff claro a la siguiente.

<br>

> Es la diferencia entre "estoy haciendo malabares con cinco bolas" y "tengo un sistema que sabe dónde está cada bola".

---

# Práctica I
## Portfolio en Astro

---

## El primer proyecto

**Repo**: `Smupk1/astro-portfolio-demo`

```bash
cd ~/workshop/astro-portfolio-demo
pnpm dev
# → localhost:4321
```

**Stack**: Astro 6 + Cloudflare Workers, deploy a edge global con un comando.

---

## ¿Por qué Astro y no Next.js?

| Astro | Next.js |
|---|---|
| HTML por default, JS opcional | JS por default, HTML opcional |
| Bundle inicial: ~0 kb JS | Bundle inicial: 80-100 kb JS |
| Hidratación selectiva (islands) | Hidratación completa |
| Ideal para sitios de contenido | Ideal para apps con mucho estado |

**Regla**: si tu sitio es 80% contenido y 20% interactividad → Astro. Si es al revés → Next.

---

## Concepto técnico clave

Astro **invierte el default** del modelo React:

- En React/Next, **todo es JS** hasta que pides explícitamente que algo sea estático (Server Components, RSC).
- En Astro, **todo es HTML** hasta que pides explícitamente que algo se hidrate (`client:load`, `client:idle`, `client:visible`).

<br>

> Esta inversión no es solo performance. Es **diseño**: cambia qué decisiones tomas sin pensar.

---

## Práctica en vivo · 5 minutos

Abre `src/styles/global.css`.

Cambia la paleta a los colores de tu universidad.

Mientras lo haces, **observa**: la latencia del hot-reload. Lo poco que tarda. Lo barato que es iterar.

<br>

¿Cuántas veces deployaste a producción para verificar un cambio de color cuando empezaste?

---

# Práctica II
## Biblioteca con Cloudflare Workers + D1 + Durable Objects

---

## El segundo proyecto

**Repo**: `Smupk1/biblioteca-cloudflare-demo`

**Stack**: Workers + D1 (SQL) + Durable Objects + Hono

Tres primitivas del plan gratuito de Cloudflare en un solo proyecto.

```bash
cd ~/workshop/biblioteca-cloudflare-demo
pnpm db:migrate:local
pnpm db:seed:local
pnpm dev
# → localhost:8787
```

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

Una clase entera puede martillar este stack sin que cueste un peso.

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
                            users,books    token → userId
```

---

## ¿Por qué un Durable Object para las sesiones?

| Opción | Problema |
|---|---|
| `Map` en memoria del Worker | Cada request puede caer en otro nodo. No persiste. |
| Cookie firmada (JWT) | Funciona, pero no se puede invalidar sin blacklist |
| D1 (tabla `sessions`) | Funciona, pero cada validación = una query SQL |
| **Durable Object** | UNA instancia global, in-memory + persistente |

<br>

> Los **Workers** son stateless por diseño. Los **DOs** son stateful por diseño. Para sesiones, rate limiting, contadores, salas — siempre DO.

---

## El modelo de consistencia de los DOs

**Single-threaded por instancia.** Si dos requests modifican la misma sesión, se serializan.

**Cero race conditions** dentro de un DO. Esto es enorme.

<br>

Compara con tener que pensar en `SELECT ... FOR UPDATE` en Postgres.

Dentro de un DO el problema **no existe** — es secuencial por diseño.

---

## La regla que generaliza

# Cada AI tool es un endpoint autenticado.

<br>

Si no expondrías la operación subyacente como un REST call sin guardias, **no puedes exponerla como un tool sin guardias.**

El schema Zod de un tool no es un boundary de seguridad. **El handler sí.**

---

# Caso de estudio
## Dos CVEs reales en 48 horas

---

## Caso #1 — `requireOrgAdmin()`

**El bug.** Cualquier miembro de una organización era tratado como **admin automáticamente**, sin importar su rol.

Parecía intencional. El patrón era viejo. Nadie lo cuestionaba.

Habría vivido en producción durante meses.

<br>

**Cómo lo cazó el sistema:** el agente de seguridad corrió una auditoría sin que se lo pidiera, encadenada con el skill de code-review. Confirmó: *este es un bug real de privilege escalation, no un design choice.*

**Lección**: *Lo que parece un feature, a veces es un CVE.*

---

## Caso #2 — Cross-tenant leak en un AI tool

**El bug.** El tool `get_ticket_detail` del asistente AI obtenía cualquier ticket por ID usando una cuenta de servicio. **Sin chequeo de ownership.**

Un usuario en organización A podía pedirle al asistente un ticket de organización B, y el asistente se lo entregaba.

<br>

**Cómo lo cazó el sistema:** durante la fase de auditoría de seguridad del rework, **antes de producción**.

**Fix:** replicar el access control del endpoint REST adentro del tool.

**Lección generaliza:** *cada AI tool es un endpoint autenticado.*

---

# Las cinco scars
## Si una charla solo muestra wins, te están vendiendo algo

---

## Scars de la misma campaña

01. **CF Workers AI lento** + malo siguiendo instrucciones. Migré a Anthropic API con fallback.

02. **`ts-node` rompió con ESM extensionless imports.** Una sesión perdida. Fix: cambiar a `tsx`.

03. **14 componentes renderizando HTML entities crudos.** MS Graph devuelve encoded. Decodificar en cada componente.

04. **`client:load` hydration mismatch con `sessionStorage`.** Switch a `client:only="react"`.

05. **Zendesk POST sin retry.** SDD no lo cazó. **El usuario sí.**

<br>

> El workflow es bueno. **No es magia.** El feedback del usuario sigue siendo irreemplazable.

---

# Las 5 reglas
## Lo que el vibecoder hace mal

---

## Regla 01

# Specs antes del código. Siempre.

Si no puedes escribir el spec, **no entiendes el cambio.**

Deja de tipear prompts.

---

## Regla 02

# Un solo modelo nunca es la respuesta.

Cada modelo tiene una fortaleza. La mezcla es el moat.

Plan, build, audit — **agentes distintos.**

---

## Regla 03

# Design is code. Merge it.

Las decisiones de arquitectura viven en version control, **al lado del código que las prueba.**

No en Notion. No en Confluence. **En el repo.**

---

## Regla 04

# "Compila" ≠ "funciona".

Verify es una fase, no una vibra.

Tests, invariants, authz checks. **No te saltes la verificación.**

---

## Regla 05

# La IA es tu junior, no tu genius.

No mergearías el PR de un junior sin leerlo.

**No mergees el de la IA tampoco.**

---

# El número

## De baseline a vivecoding

<br>

# 6 meses → 1 mes

<br>

Producción. Multi-tenant. 78 tests pasando. Dos auditorías de seguridad.

**La velocidad no vino de saltarse pasos.**

Vino de **paralelizar los pasos correctos con los modelos correctos.**

---

# Tres cosas para llevarse a casa

---

<!-- _class: center -->

## 01 · La Tesis

# Disciplina le gana a vibras.

Specs, design, TDD, verify.

El SDLC clásico — ahora ejecutable.

---

<!-- _class: center -->

## 02 · El Stack

# El modelo correcto para el trabajo correcto.

Un solo modelo nunca es la respuesta.

La mezcla es el moat.

---

<!-- _class: center -->

## 03 · La Matemática

# La IA es un amplificador.

No reemplaza al ingeniero.

Hace al ingeniero entrenado **6× más rápido.**

---

<!-- _class: center -->

<br><br>

# Vibecoding es roleplay.

# Vivecoding es una campaña con disciplina.

<br>

<span class="mono" style="color:#666">vivecoding.dev</span>

---

## Recursos

**Repos del workshop:**
- `github.com/Smupk1/astro-portfolio-demo`
- `github.com/Smupk1/biblioteca-cloudflare-demo`

**Manifiesto completo:**
- vivecoding.dev/writing/vibecoding-vs-vivecoding

**Stack del workshop:**
- [Astro](https://docs.astro.build) · [Cloudflare Workers](https://developers.cloudflare.com/workers/) · [Hono](https://hono.dev/) · [Drizzle](https://orm.drizzle.team/)

---

<!-- _class: center -->

# Preguntas

<br>

Disagree publicly. I'll listen.

<br>

<span class="mono" style="color:#666;font-size:14px">Samuel Cala · linkedin.com/in/samuelsapontec</span>
