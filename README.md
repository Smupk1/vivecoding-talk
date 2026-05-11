# Vibe Coding · Workshop

**Workshop de 90 minutos para estudiantes universitarios avanzados de CS** sobre vibe coding como metodología — usando dos proyectos reales como demos hands-on:

- 🎨 [`astro-portfolio-demo`](https://github.com/Smupk1/astro-portfolio-demo) — sitio estático en Astro deployado a Cloudflare Workers
- 📚 [`biblioteca-cloudflare-demo`](https://github.com/Smupk1/biblioteca-cloudflare-demo) — CRUD full-stack con Workers + D1 + Durable Objects

> Esta NO es una charla sobre "cómo copiar y pegar de ChatGPT". Es una charla sobre **cómo dirigir modelos para construir sistemas reales sin perder los fundamentos** — y, sobre todo, cuándo conviene NO usar IA.

---

## Contenido del repo

```
vivecoding-talk/
├── slides-es.md         # Deck en español (Marp)
├── slides-en.md         # Deck en inglés (Marp)
├── speaker-notes-es.md  # Guion ampliado en español: qué decir en cada bloque
├── speaker-notes-en.md  # Guion ampliado en inglés
├── setup.md             # Prerequisites para que los estudiantes vengan preparados
└── README.md
```

---

## Cómo exportar las slides a PDF / HTML / PPT

Las slides están escritas en **[Marp](https://marp.app/)**, un dialecto de Markdown que se renderiza a presentaciones reales.

### Opción A: VS Code (recomendado para iterar)

1. Instalá la extensión **[Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode)**
2. Abrí `slides-es.md`
3. Click en el ícono "Open Preview to the Side"
4. Para exportar: paleta de comandos → "Marp: Export slide deck..." → PDF / HTML / PPTX

### Opción B: CLI

```bash
# Instalar Marp CLI globalmente
pnpm add -g @marp-team/marp-cli

# Exportar a PDF
marp slides-es.md --pdf

# Exportar a HTML standalone (perfecto para presentar desde el navegador)
marp slides-es.md --html

# Exportar a PowerPoint editable
marp slides-es.md --pptx
```

---

## Cómo dar la charla

1. **Una semana antes**: mandales `setup.md` a los estudiantes para que vengan con todo instalado.
2. **El día**: abrí `speaker-notes-es.md` en un monitor secundario; la deck en el principal.
3. **En los hands-on (bloques 4 y 5)**: pediles que cloneen ANTES de cada bloque, no durante — `pnpm install` come tiempo en aula.
4. **Cuando alguien pregunte algo que no sabés**: decilo. Es parte del mensaje — vibe coding bien hecho incluye admitir lo que no sabés.

---

## Licencia

MIT — clonalo, adaptalo, dictalo en tu universidad. Si lo usás, me alegra saber dónde (no obligatorio).
