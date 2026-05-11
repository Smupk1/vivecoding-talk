# Setup · Para estudiantes / For students

> 🇪🇸 Ven con esto instalado **antes del workshop**. Si llegas sin esto, el `pnpm install` te va a comer la mitad del bloque hands-on.
>
> 🇬🇧 Have this installed **before the workshop**. If you arrive without it, `pnpm install` will eat half the hands-on block.

---

## 🇪🇸 Requisitos previos

### 1. Node.js v20+

```bash
node --version   # debería decir v20.x.x o más
```

Si no lo tienes: [nodejs.org](https://nodejs.org/) o usa [fnm](https://github.com/Schniz/fnm) / [nvm](https://github.com/nvm-sh/nvm).

### 2. pnpm

```bash
npm install -g pnpm
pnpm --version
```

### 3. Git + GitHub CLI

```bash
git --version
gh --version

# Autenticar gh (necesitás cuenta de GitHub)
gh auth login
```

### 4. Cuenta en Cloudflare (gratuita)

[dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up) - solo para el bloque de deploy. **No piden tarjeta** para el plan free.

### 5. Editor con plugin para AI coding (opcional pero ideal)

Elige UNA:
- **[Cursor](https://cursor.sh/)** - VS Code fork con AI integrado (recomendado para el workshop)
- **[VS Code + Continue](https://www.continue.dev/)** - alternativa open-source
- **[Claude Code](https://www.anthropic.com/claude-code)** - CLI agéntico

### 6. Clonar los repos (hazlo en casa)

```bash
mkdir -p ~/workshop && cd ~/workshop

git clone https://github.com/Smupk1/astro-portfolio-demo.git
cd astro-portfolio-demo && pnpm install && cd ..

git clone https://github.com/Smupk1/biblioteca-cloudflare-demo.git
cd biblioteca-cloudflare-demo && pnpm install && cd ..
```

### Verificación final

```bash
cd ~/workshop/astro-portfolio-demo && pnpm dev
# debería levantar en localhost:4321 - Ctrl+C para cortar

cd ~/workshop/biblioteca-cloudflare-demo
pnpm db:migrate:local
pnpm db:seed:local
pnpm dev
# debería levantar en localhost:8787 - Ctrl+C para cortar
```

Si los dos comandos arrancaron sin error, estás listo. ✅

> *Vibecoding es roleplay. Vivecoding es una campaña con disciplina.*

---

## 🇬🇧 Prerequisites

### 1. Node.js v20+

```bash
node --version   # should say v20.x.x or higher
```

If you don't have it: [nodejs.org](https://nodejs.org/) or use [fnm](https://github.com/Schniz/fnm) / [nvm](https://github.com/nvm-sh/nvm).

### 2. pnpm

```bash
npm install -g pnpm
pnpm --version
```

### 3. Git + GitHub CLI

```bash
git --version
gh --version

# Auth gh (you need a GitHub account)
gh auth login
```

### 4. Cloudflare account (free)

[dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up) - only for the deploy block. **No credit card required** for the free plan.

### 5. AI-enabled editor (optional but ideal)

Pick ONE:
- **[Cursor](https://cursor.sh/)** - VS Code fork with AI built-in (recommended for the workshop)
- **[VS Code + Continue](https://www.continue.dev/)** - open-source alternative
- **[Claude Code](https://www.anthropic.com/claude-code)** - agentic CLI

### 6. Clone the repos (at home)

```bash
mkdir -p ~/workshop && cd ~/workshop

git clone https://github.com/Smupk1/astro-portfolio-demo.git
cd astro-portfolio-demo && pnpm install && cd ..

git clone https://github.com/Smupk1/biblioteca-cloudflare-demo.git
cd biblioteca-cloudflare-demo && pnpm install && cd ..
```

### Final check

```bash
cd ~/workshop/astro-portfolio-demo && pnpm dev
# should start on localhost:4321 - Ctrl+C to stop

cd ~/workshop/biblioteca-cloudflare-demo
pnpm db:migrate:local
pnpm db:seed:local
pnpm dev
# should start on localhost:8787 - Ctrl+C to stop
```

If both started without error, you're set. ✅
