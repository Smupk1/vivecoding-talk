# Vivecoding · University Workshop

**Workshop universitario de 90 minutos** sobre Vivecoding — la metodología de ingeniería asistida por IA que practico en IT Audit Labs.

Este repo es la versión **académica** del manifiesto que vive en [vivecoding.dev/writing/vibecoding-vs-vivecoding](https://vivecoding.dev/writing/vibecoding-vs-vivecoding), adaptada para estudiantes universitarios de CS, años superiores. Usa dos proyectos reales como práctica hands-on:

- 🎨 [`astro-portfolio-demo`](https://github.com/Smupk1/astro-portfolio-demo) — sitio estático en Astro deployado a Cloudflare Workers
- 📚 [`biblioteca-cloudflare-demo`](https://github.com/Smupk1/biblioteca-cloudflare-demo) — CRUD full-stack con Workers + D1 + Durable Objects

> **La tesis**: Vibecoding es roleplay. Vivecoding es una campaña con disciplina.

---

## Por qué este workshop existe

La industria está dividida entre dos campos extremos sobre la IA en ingeniería:

- **Los evangelistas**: *"prompt and ship, el código no importa"*
- **Los puristas**: *"no toques la IA, vas a perder los fundamentos"*

**Vivecoding** es la tercera vía: tratar a la IA como el junior más poderoso que has manejado, y aplicarle el mismo rigor de ingeniería que aplicarías a cualquier otro contribuidor.

Este workshop le enseña a estudiantes universitarios cómo construir con IA **sin saltarse los fundamentos**.

---

## Contenido del repo

```
vivecoding-talk/
├── slides-es.md         # Deck en español (Marp)
├── slides-en.md         # Deck en inglés (Marp)
├── speaker-notes-es.md  # Guion ampliado: qué decir en cada bloque
├── speaker-notes-en.md  # Speaker notes in English
├── setup.md             # Prerequisites bilingüe para estudiantes
└── README.md
```

---

## Estructura del workshop (90 min)

| Min | Bloque | Contenido |
|---|---|---|
| 0-5 | **Setup** | Verificar que todos arranquen `pnpm dev` |
| 5-10 | **Cold open** | *"Did you vibe code it?"* — la historia del whiteboard |
| 10-20 | **Acto I: Vibecoding vs Vivecoding** | El cuadro comparativo. La tesis. |
| 20-30 | **Acto II: El stack** | Multi-modelo. Pipeline SDD. Cómo escala. |
| 30-45 | **Práctica 1: Astro Portfolio** | Hands-on. Islands architecture. |
| 45-70 | **Práctica 2: Biblioteca CRUD** | Workers + D1 + DO. *"Every AI tool is an authenticated endpoint."* |
| 70-78 | **Casos de estudio** | Las 2 CVEs reales cazadas en 48 horas |
| 78-82 | **Las 5 scars** | Si una charla solo muestra wins, te están vendiendo algo |
| 82-87 | **Las 5 reglas** | Specs · Multi-modelo · Design is code · Verify · La IA es tu junior |
| 87-90 | **El número + cierre** | 6 meses → 1 mes. Tres takeaways. |

---

## Cómo exportar las slides

Las slides están en **[Marp](https://marp.app/)** — Markdown que se renderiza a PDF/HTML/PPTX.

### Opción A: VS Code (recomendado para iterar)

1. Instalar la extensión **[Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode)**
2. Abrir `slides-es.md`
3. Click en "Open Preview to the Side"
4. Exportar: paleta de comandos → "Marp: Export slide deck..." → PDF / HTML / PPTX

### Opción B: CLI

```bash
# Instalar Marp CLI
pnpm add -g @marp-team/marp-cli

# Exportar a PDF
marp slides-es.md --pdf

# Exportar a HTML standalone (ideal para presentar)
marp slides-es.md --html

# Exportar a PowerPoint editable
marp slides-es.md --pptx
```

---

## Cómo dar la charla

1. **Una semana antes**: mandar `setup.md` a los estudiantes para que vengan con todo instalado.
2. **El día**: abrir `speaker-notes-es.md` en un monitor secundario; la deck en el principal.
3. **En los hands-on (bloques 4 y 5)**: pedirles que cloneen ANTES de cada bloque, no durante — `pnpm install` come tiempo en aula.
4. **Cuando alguien pregunte algo que no sé**: decirlo. Es parte del mensaje — vivecoding bien hecho incluye admitir lo que no sabes.

---

## El manifiesto completo

Esta charla es la versión académica. El manifiesto técnico completo, con el DAG, los model assignments, las dos CVEs en detalle, las cinco scars, y la arquitectura del ITALPortal vive en:

**[vivecoding.dev/writing/vibecoding-vs-vivecoding](https://vivecoding.dev/writing/vibecoding-vs-vivecoding)**

---

## Licencia

MIT — clona, adapta, dicta esta charla en tu universidad. Si la usas, me alegra saber dónde.

---

> *Vibecoding es roleplay. Vivecoding es una campaña con disciplina.*
>
> — **Samuel Cala**, IT Audit Labs · [vivecoding.dev](https://vivecoding.dev)
