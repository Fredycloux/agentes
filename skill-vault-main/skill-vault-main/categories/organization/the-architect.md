---
name: the-architect
source_url: https://www.tododeia.com/community/the-architect
source_type: github
category: organization
safety_rating: caution
date_added: 2026-04-16
version: 1.0.0
tags: [architecture, planning, blueprint, claude-md, project-design, saas, webapp]
---

# The Architect

## Description

Consultor sénior de diseño de software que entrevista al usuario sobre su proyecto y genera un blueprint de 16 secciones listo para que Claude Code construya el proyecto de forma autónoma. Flujo de 4 fases: Discovery (preguntas conversacionales), Deep Dive (stack y decisiones técnicas), Architecture (propuesta con rationale) y Generate (escribe el archivo `output/<nombre>-blueprint.md`). El blueprint incluye un `CLAUDE.md` completo y un orden de construcción numerado paso a paso. Soporta modo rápido "just build it" con 3 preguntas esenciales.

## Security Analysis

- **Rating**: caution
- **Allowed Tools**: no especificados explícitamente (usa el set completo de Claude Code)
- **Findings**:
  - Usa WebFetch y WebSearch al comparar tecnologías (llamadas a internet documentadas)
  - Escribe archivos únicamente en `output/` dentro del proyecto — rutas acotadas y esperadas
  - Sin comandos shell destructivos
  - Puede invocar sub-skills como `/deep-research`, `/ui-ux-pro-max`, `/find-skills` — amplía el scope indirectamente
  - Sin acceso a credenciales ni variables de entorno
  - Sin ejecución dinámica de código
  - Descripción coincide con el comportamiento real
  - Riesgo moderado: herramientas web + sub-skills opcionales. Revisar antes de usar en proyectos con información sensible.

## Install Command

```bash
# Abrir Claude Code en la carpeta del proyecto
cd "C:/01. Repositorios/Agentes/the-architect-main/the-architect-main"
claude
# El agente se activa automáticamente via CLAUDE.md
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del CLAUDE.md</summary>

```markdown
Agente The Architect — genera blueprints de 16 secciones para proyectos de software.
Archivo completo en: C:/01. Repositorios/Agentes/the-architect-main/the-architect-main/CLAUDE.md
```

</details>

## Notes

El modo "just build it" genera el blueprint con solo 3 preguntas (qué es, para quién, preferencia de stack). El archivo generado en `output/` sirve directamente como CLAUDE.md para el proyecto nuevo.
