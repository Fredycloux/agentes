---
name: humanizalo
source_url: https://www.tododeia.com/community/humanizalo
source_type: github
category: productivity
safety_rating: safe
date_added: 2026-04-16
version: 1.0.0
tags: [writing, text-editing, humanize, ai-detection, copywriting]
---

# Humanízalo

## Description

Transforma texto generado por IA en escritura que suena auténticamente humana. Detecta y elimina 40 patrones de escritura robótica distribuidos en 5 categorías: inflación de contenido, vocabulario, estructura, formato y artefactos de comunicación. Incluye inyección de personalidad, un sistema de puntuación de 6 dimensiones (umbral 42/60) y un bucle de auto-auditoría de hasta 3 iteraciones. Usar después de que Claude genere cualquier texto que vaya a ser leído o publicado por personas reales.

## Security Analysis

- **Rating**: safe
- **Allowed Tools**: Read, Write, Edit, Grep, Glob, AskUserQuestion
- **Findings**:
  - Allowed-tools scope: minimal y específico — solo operaciones de lectura/escritura de archivos y preguntas al usuario
  - Sin comandos shell destructivos
  - Sin llamadas de red — 100% local
  - Escribe únicamente en archivos que el usuario ya tiene abiertos o proporciona
  - Sin acceso a variables de entorno ni credenciales
  - Sin ejecución dinámica de código
  - Sin ofuscación en el contenido del skill
  - Descripción coincide exactamente con el comportamiento real

## Install Command

```bash
# Copiar SKILL.md a tus comandos de Claude Code
cp "C:/01. Repositorios/Agentes/humanizalo-main/humanizalo-main/SKILL.md" \
   "C:/01. Repositorios/.claude/skills/humanizalo/SKILL.md"
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del SKILL.md</summary>

```markdown
Skill para humanizar texto IA. Detecta 40 patrones, aplica inyección de personalidad,
puntúa en 6 dimensiones y entrega texto revisado con score final.
Ver archivo SKILL.md completo en: C:/01. Repositorios/Agentes/humanizalo-main/humanizalo-main/SKILL.md
```

</details>

## Notes

Ideal para usar después de generar emails, documentación técnica, posts o cualquier texto antes de publicarlo. El bucle de 3 iteraciones garantiza que el texto supere el umbral de 42/60 puntos en las 6 dimensiones de autenticidad.
