---
name: editor-pro-max
source_url: https://www.tododeia.com/community/editor-pro-max
source_type: github
category: design-ui
safety_rating: caution
date_added: 2026-04-16
version: 1.0.0
tags: [video, editor, remotion, ffmpeg, tiktok, reels, youtube, instagram, subtitles]
---

# Editor Pro Max

## Description

Estudio completo de edición de video basado en Remotion (React + TypeScript). El usuario describe el video en lenguaje natural y el agente escribe componentes React que se compilan a video. Incluye 25+ componentes reutilizables (AnimatedTitle, LowerThird, ParticleField, TransitionPresets), 9 templates predefinidos (TikTokVideo, InstagramReel, YouTubeShort, Presentation, Announcement, etc.), auto-setup de dependencias al abrir, y scripts de batch-render para múltiples plataformas. Genera subtítulos automáticos via Whisper.cpp y elimina fondos via FFmpeg. Preview en Remotion Studio (localhost:3000).

## Security Analysis

- **Rating**: caution
- **Allowed Tools**: Bash, Read, Write, Edit (implícito via CLAUDE.md)
- **Findings**:
  - Bash: ejecuta `npm install` automáticamente al primer uso — sin preguntar al usuario (comportamiento documentado)
  - Bash: `npx remotion render` — renderizado de video local, computacionalmente intensivo
  - Bash: `./scripts/batch-render.sh` — scripts de batch documentados
  - Requiere Node.js 20+ — dependencia documentada
  - FFmpeg y Whisper.cpp: dependencias externas opcionales para funciones avanzadas
  - Escribe archivos en `src/compositions/` y `out/` — rutas acotadas y esperadas
  - Sin llamadas de red en el flujo principal
  - Sin acceso a credenciales ni variables de entorno
  - Sin exfiltración de datos — todo local
  - Descripción coincide con el comportamiento real

## Install Command

```bash
cd "C:/01. Repositorios/Agentes/editor-pro-max-main/editor-pro-max-main"
# npm install se ejecuta automáticamente al abrir Claude Code
claude
npm run dev   # Remotion Studio en http://localhost:3000
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del CLAUDE.md</summary>

```markdown
Editor Pro Max — editor de video con Remotion + React.
Archivo completo en: C:/01. Repositorios/Agentes/editor-pro-max-main/editor-pro-max-main/CLAUDE.md
```

</details>

## Notes

Para renderizar: `npx remotion render <CompositionId> out/video.mp4`. Para batch en múltiples plataformas: `./scripts/batch-render.sh Showcase youtube tiktok square`. Requiere Node.js 20+ (LTS recomendado).
