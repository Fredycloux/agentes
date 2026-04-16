---
name: open-carrusel
source_url: https://www.tododeia.com/community/open-carrusel
source_type: github
category: design-ui
safety_rating: caution
date_added: 2026-04-16
version: 1.0.0
tags: [instagram, carousel, social-media, nextjs, puppeteer, design, branding, export]
---

# Open Carrusel

## Description

Constructor de carruseles de Instagram con IA. Arquitectura Next.js 16 + React 19 + TypeScript con panel de chat (izquierda), preview del carrusel (centro) y filmstrip de slides (abajo). Genera múltiples slides en paralelo desde descripciones textuales, permite reordenar con drag-and-drop y exporta imágenes PNG a dimensiones exactas de Instagram via Puppeteer (1:1 1080×1080, 4:5 1080×1350, 9:16 1080×1920). Almacena configuración de marca (colores, fuentes Google, logo) en JSON local. Claude se ejecuta como subprocess con acceso a Bash y WebFetch para llamar a las API routes locales.

## Security Analysis

- **Rating**: caution
- **Allowed Tools**: Bash (subprocess con --allowedTools Bash,WebFetch), Read, Write
- **Findings**:
  - Bash: ejecuta `npm install` y `npm run dev` — instalación y arranque documentados
  - Claude subprocess: `--allowedTools Bash WebFetch` — scope acotado, llama a `curl localhost:3000/api/*`
  - WebFetch: solo llama a `localhost:3000/api/` — red local únicamente
  - Puppeteer: toma screenshots de slides en iframes — sin acceso a internet externo
  - iframes con `sandbox=""` — sin ejecución de JavaScript en slides
  - Uploads limitados a PNG/JPG/WebP, máximo 10MB
  - Almacenamiento en `/data/*.json` con async-mutex y escrituras atómicas — seguro
  - Sin credenciales ni API keys requeridas
  - Sin exfiltración de datos
  - Descripción coincide con el comportamiento real

## Install Command

```bash
cd "C:/01. Repositorios/Agentes/open-carrusel-main/open-carrusel-main"
npm install
npm run dev   # Servidor en http://localhost:3000
# Claude Code en esa carpeta controla el agente via chat
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del CLAUDE.md</summary>

```markdown
Open Carrusel — constructor de carruseles Instagram con IA.
Archivo completo en: C:/01. Repositorios/Agentes/open-carrusel-main/open-carrusel-main/CLAUDE.md
```

</details>

## Notes

Máximo 10 slides por carrusel. La configuración de marca se guarda en `/data/brand.json` y persiste entre sesiones. La exportación genera un ZIP con todos los slides en PNG.
