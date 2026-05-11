# Vivecoding · University Workshop

**Workshop universitario de 90 minutos** sobre Vivecoding — la metodología de ingeniería asistida por IA que practico en IT Audit Labs.

Este repo es la versión **académica** del manifiesto que vive en [vivecoding.dev/writing/vibecoding-vs-vivecoding](https://vivecoding.dev/writing/vibecoding-vs-vivecoding), adaptada para estudiantes universitarios de CS, años superiores. Usa dos proyectos reales como práctica hands-on:

- 🎨 [`astro-portfolio-demo`](https://github.com/Smupk1/astro-portfolio-demo) — sitio estático en Astro deployado a Cloudflare Workers
- 📚 [`biblioteca-cloudflare-demo`](https://github.com/Smupk1/biblioteca-cloudflare-demo) — CRUD full-stack con Workers + D1 + Durable Objects

> **La tesis**: Vibecoding es improvisación. Vivecoding es ingeniería.

---

## Contenido del repo

```
vivecoding-talk/
├── deck/
│   ├── index.html       # Deck HTML standalone (19 slides)
│   └── deck-stage.js    # Motor de navegación + animaciones
├── setup.md             # Prerequisites bilingüe para estudiantes
├── LICENSE
└── README.md
```

El deck está construido sobre el mismo formato HTML/CSS/JS que el deck oficial de Vivecoding en [vivecoding.dev](https://vivecoding.dev) — mismo estilo visual, mismas animaciones, mismas tipografías (Space Grotesk + JetBrains Mono).

---

## Estructura del workshop (90 min · 19 slides)

| # | Slide | Bloque |
|---|---|---|
| 01 | Title | Apertura |
| 02 | The Confession | "For years I pronounced it vibecoding" |
| 03 | The Thesis | Vibecoding vs Vivecoding |
| 04 | Specialized Agents | RAG memory · Bard · Auditor |
| 05 | SDD Agents | explore · spec · design · apply · verify |
| 06 | The Stack | Gemini · Claude · Workers AI · Codex · CodeRabbit |
| 07 | The SDD Workflow | El DAG |
| 08 | Meta-commands | `/sdd-new` · `/sdd-continue` · `/sdd-ff` |
| **09** | **Hands-on 1: Astro Portfolio** | 15 min de práctica |
| **10** | **Hands-on 2: Biblioteca CRUD** | 25 min de práctica |
| **11** | **DO + AI Tool Security** | Por qué DO, every AI tool is auth'd |
| 12 | ITALPortal | Case study real |
| 13 | The Number | 6 meses → 1 mes |
| 14 | CVE #1 | `requireOrgAdmin()` privilege escalation |
| 15 | CVE #2 | Cross-tenant leak en AI tool |
| 16 | The Honest Scars | 5 cosas que no salieron bien |
| 17 | Hot Takes | Las 5 reglas |
| 18 | Three Takeaways | Tesis · Stack · Math |
| 19 | Thanks · Q&A | Cierre |

Los slides 09-11 son **nuevos respecto al deck oficial** — adaptados para el contexto universitario y para integrar los dos repos de práctica.

---

## Cómo presentar el deck

El deck es **HTML standalone** — no necesita Marp, Reveal, ni ningún sistema externo.

### Localmente

```bash
cd deck
python3 -m http.server 8000
# Abre http://localhost:8000 en el navegador
```

### Cómo navegar

- **Flechas ← →** para cambiar de slide
- **Espacio** para avanzar
- **F** para fullscreen
- **N** para abrir el panel de speaker notes

Las notas del orador están embebidas en el HTML (`<script id="speaker-notes">`) y aparecen al presionar `N` o en una segunda ventana si abres la URL con `?notes`.

### Para exportar a PDF

Abre el deck en Chrome, fullscreen, y usa `Cmd+P` → "Save as PDF" con orientación horizontal. Cada slide es 1920×1080.

---

## Cómo dar la charla

1. **Una semana antes**: manda `setup.md` a los estudiantes para que vengan con todo instalado.
2. **El día**: abre el deck en un monitor; las notas en el otro (o ventana aparte con `?notes`).
3. **En los hands-on (slides 9-11)**: pide que cloneen ANTES de cada bloque. `pnpm install` come tiempo en aula.
4. **Cuando alguien pregunte algo que no sabes**: dilo. Es parte del mensaje — vivecoding bien hecho incluye admitir lo que no sabes.

---

## El manifiesto completo

Esta charla es la versión académica. El manifiesto técnico completo, con el DAG, los model assignments, las dos CVEs en detalle, las cinco scars, y la arquitectura del ITALPortal vive en:

**[vivecoding.dev/writing/vibecoding-vs-vivecoding](https://vivecoding.dev/writing/vibecoding-vs-vivecoding)**

---

## Licencia

MIT — clona, adapta, dicta esta charla en tu universidad.

---

> *Vibecoding es improvisación. Vivecoding es ingeniería.*
>
> — **Samuel Cala**, IT Audit Labs · [vivecoding.dev](https://vivecoding.dev)
