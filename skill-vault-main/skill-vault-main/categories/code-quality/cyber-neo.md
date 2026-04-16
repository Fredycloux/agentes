---
name: cyber-neo
source_url: https://www.tododeia.com/community/cyber-neo
source_type: github
category: code-quality
safety_rating: safe
date_added: 2026-04-16
version: 1.0.0
tags: [security, audit, owasp, cwe, vulnerabilities, secrets, readonly, python, javascript, typescript]
---

# Cyber Neo

## Description

Agente de auditoría de seguridad que despliega 5 subagentes en paralelo para analizar proyectos locales. Cubre OWASP 2025 Top 10, CWE Top 25, más de 60 patrones de detección de secretos, y dominios especializados: autenticación, criptografía, seguridad web, manejo de errores, logging, CI/CD y supply chain. Funciona en modo completamente de solo lectura — nunca modifica el proyecto auditado. Genera un reporte priorizado en Markdown en el escritorio. Compatible con proyectos JavaScript, TypeScript y Python. Scripts Python usan solo la biblioteca estándar.

## Security Analysis

- **Rating**: safe
- **Allowed Tools**: Grep, Read, Bash (scripts Python de solo lectura)
- **Findings**:
  - Diseño explícitamente READ-ONLY — nunca modifica archivos del proyecto auditado
  - Bash: ejecuta scripts Python con `python scan_secrets.py <dir>` y `python check_lockfiles.py <dir>` — solo lectura, output JSON a stdout
  - Scripts Python: solo usan biblioteca estándar (sin pip), aceptan directorio como argumento, no modifican nada
  - Sin llamadas de red — análisis 100% local
  - Sin acceso a credenciales ni variables de entorno
  - Sin exfiltración de datos
  - Sin ejecución dinámica de código (`eval`, `exec`)
  - Sin comandos destructivos
  - Descripción coincide exactamente con el comportamiento real
  - El comportamiento de solo lectura está reforzado en múltiples lugares del CLAUDE.md

## Install Command

```bash
# Desde el proyecto a auditar, en Claude Code:
/cyber-neo
# O abrir Claude Code en la carpeta del agente:
cd "C:/01. Repositorios/Agentes/cyber-neo-main/cyber-neo-main"
claude
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original</summary>

```markdown
Cyber Neo — auditoría de seguridad multi-agente OWASP 2025.
Skill en: C:/01. Repositorios/Agentes/cyber-neo-main/cyber-neo-main/skills/cyber-neo/SKILL.md
```

</details>

## Notes

Usar antes de cualquier deploy a producción. Compatible con proyectos JS, TypeScript y Python. El reporte incluye CWE ID, categoría OWASP 2025, severity score y remediation con ejemplos de código. Herramientas externas (Semgrep, Trivy, Gitleaks) son opcionales — el agente funciona sin ellas.
