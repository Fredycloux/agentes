---
name: claude-web-builder
source_url: https://www.tododeia.com/community/claude-web-builder
source_type: github
category: web-development
safety_rating: caution
date_added: 2026-04-16
version: 1.0.0
tags: [landing-page, nextjs, tailwind, shadcn, vercel, deploy, seo, accessibility, web]
---

# Claude Web Builder

## Description

Constructor automatizado de landing pages profesionales con Next.js 15+, Tailwind CSS v4, shadcn/ui, TypeScript y Framer Motion. Flujo de 6 fases: Discovery (cuestionario en 4 rondas), Design System (colores/fuentes via ui-ux-pro-max), Scaffold (crea el proyecto Next.js automáticamente), Build (escribe todos los componentes), Preview & QA (dev server + screenshots + SEO audit) y Deploy (Vercel sandbox sin cuenta). Incluye 13 skills bundleados. Responde en español si el usuario escribe en español. Auto-piloto total en Fases 3-4: sin preguntas, solo construye.

## Security Analysis

- **Rating**: caution
- **Allowed Tools**: Bash, Read, Write, Edit, WebFetch, WebSearch (via sub-skills)
- **Findings**:
  - Bash: ejecuta `npx create-next-app`, `npm install`, `npx shadcn`, `npm run dev`, `npm run build` — instalación y desarrollo documentados
  - Bash: ejecuta `bash .claude/skills/vercel-deploy/scripts/deploy.sh site` — script de deploy a Vercel sandbox
  - WebFetch/WebSearch: via sub-skills `deep-research` y `web-reader` para investigar industrias o analizar URLs de referencia — documentado
  - Deploy: sube el build a Vercel sandbox (red externa) — comportamiento explícito y esperado
  - Escribe archivos únicamente en `site/` — directorio acotado
  - Sin acceso a credenciales del usuario (el deploy a Vercel sandbox es anónimo)
  - Scripts de deploy son open source y auditables
  - Sin obfuscación
  - Descripción coincide con el comportamiento real
  - Riesgo moderado: despliega código a internet. Verificar contenido antes de deploy.

## Install Command

```bash
cd "C:/01. Repositorios/Agentes/claude-webkit-main/claude-webkit-main"
claude
# El agente inicia automáticamente el cuestionario en español
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del CLAUDE.md</summary>

```markdown
Claude Web Builder — constructor de landing pages con Next.js + Tailwind.
Archivo completo en: C:/01. Repositorios/Agentes/claude-webkit-main/claude-webkit-main/CLAUDE.md
```

</details>

## Notes

El deploy a Vercel sandbox no requiere cuenta. Genera una URL preview pública + una URL para reclamar permanentemente con cuenta gratuita. Checklist de calidad incluye: WCAG AA, Core Web Vitals, SEO y copy humanizado.
