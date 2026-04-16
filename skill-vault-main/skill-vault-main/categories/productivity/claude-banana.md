---
name: claude-banana
source_url: https://www.tododeia.com/community/claude-banana
source_type: github
category: productivity
safety_rating: safe
date_added: 2026-04-16
version: 1.0.0
tags: [image-prompts, ai-images, prompt-engineering, gemini, midjourney, dall-e, creative]
---

# Claude Banana

## Description

Agente de ingeniería de prompts para generadores de imágenes IA. Toma una descripción simple del usuario, hace 2-4 preguntas de clarificación (mood, dominio, elementos clave) y construye un prompt optimizado usando la fórmula de 7 componentes: sujeto, estilo visual, entorno, iluminación, acción, ángulo de cámara y texturas. Incluye 9 modos de dominio (cine, producto, retrato, moda, UI, logo, paisaje, abstracto, infografías) y un catálogo de 70+ técnicas. Compatible con Gemini/Google Flow, Midjourney, DALL-E y Stable Diffusion. Permite iteración incremental sin empezar desde cero.

## Security Analysis

- **Rating**: safe
- **Allowed Tools**: Read (base de conocimiento), AskUserQuestion (implícito)
- **Findings**:
  - Sin comandos shell en el flujo principal
  - Sin llamadas de red — genera prompts localmente usando base de conocimiento en `/knowledge`
  - Scripts Python opcionales en `/scripts` requieren `google-generativeai` — solo si el usuario los ejecuta manualmente
  - Sin acceso a credenciales ni variables de entorno en el flujo principal
  - Sin escritura de archivos del usuario — solo genera texto de prompt
  - Sin obfuscación
  - Descripción coincide con el comportamiento real
  - Los scripts opcionales son estándar y documentados

## Install Command

```bash
# Abrir Claude Code en la carpeta del agente
cd "C:/01. Repositorios/Agentes/claude-banana-main/claude-banana-main"
claude
# Describir la imagen que quieres crear y el agente optimiza el prompt
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del CLAUDE.md</summary>

```markdown
Claude Banana — agente de prompt engineering para imágenes IA.
Archivo completo en: C:/01. Repositorios/Agentes/claude-banana-main/claude-banana-main/CLAUDE.md
```

</details>

## Notes

Reglas críticas del agente: nunca usar keywords baneadas como "4K", "masterpiece", "hyperrealistic". Usar prosa narrativa, no listas de palabras separadas por comas. Límite de 25 caracteres para texto en imágenes.
