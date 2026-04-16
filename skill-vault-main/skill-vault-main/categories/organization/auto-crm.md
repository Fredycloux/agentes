---
name: auto-crm
source_url: https://www.tododeia.com/community/auto-crm
source_type: github
category: organization
safety_rating: caution
date_added: 2026-04-16
version: 1.0.0
tags: [crm, sales, leads, kanban, sqlite, nextjs, mcp, webhook, contacts]
---

# Auto-CRM

## Description

CRM completo y local construido con Next.js 16, React 19, TypeScript, Tailwind CSS v4, SQLite y Drizzle ORM. Incluye dashboard con métricas, tablero kanban drag-and-drop, base de datos de contactos con scoring de temperatura (frío/tibio/caliente), historial de actividades y webhook para capturar leads externos. Se controla mediante comandos en lenguaje natural desde Claude Code. Tres modos de IA: Terminal (sin API key), API (clasificación inline) y MCP (Claude Desktop). Corre 100% local — ningún dato sale de la máquina.

## Security Analysis

- **Rating**: caution
- **Allowed Tools**: Bash, Read, Write, Edit (implícito via CLAUDE.md)
- **Findings**:
  - Bash: ejecuta `npm install`, `npm run dev`, `npm run init:seed` — instalación y arranque documentados
  - Base de datos SQLite local en `data/crm.db` — sin servicios externos obligatorios
  - API routes en localhost:3000 — red local únicamente
  - Webhook en `/api/webhook` acepta conexiones externas si el usuario lo expone — riesgo bajo pero depende de configuración del usuario
  - Variables de entorno opcionales: `ANTHROPIC_API_KEY`, `RESEND_API_KEY` — no requeridas para uso básico
  - Sin exfiltración de datos — todo local
  - Integración MCP opcional — amplía el scope si se habilita
  - Sin comandos destructivos ni obfuscación
  - Descripción coincide con el comportamiento real

## Install Command

```bash
cd "C:/01. Repositorios/Agentes/auto-crm-main/auto-crm-main"
npm install
npm run init:seed   # Base de datos con datos demo
npm run dev         # Servidor en http://localhost:3000
# Luego en Claude Code: /setup
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del CLAUDE.md</summary>

```markdown
Auto-CRM — CRM local completo con Next.js + SQLite.
Archivo completo en: C:/01. Repositorios/Agentes/auto-crm-main/auto-crm-main/CLAUDE.md
```

</details>

## Notes

Comandos clave: `/setup` (configurar), `/add-lead` (agregar lead), `/analyze-pipeline` (análisis), `/daily-briefing` (resumen del día), `/import-contacts` (importar CSV). Docker disponible para deploy local permanente.
