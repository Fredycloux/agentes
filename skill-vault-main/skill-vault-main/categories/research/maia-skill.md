---
name: investment-analysis
source_url: https://www.tododeia.com/community/maia-skill
source_type: github
category: research
safety_rating: caution
date_added: 2026-04-16
version: 2.0.0
tags: [finance, investment, markets, crypto, stocks, forex, commodities, multi-agent, dashboard]
---

# Maia Skill — Investment Analysis

## Description

Sistema multi-agente de investigación financiera que despliega 5 agentes especializados en paralelo: Crypto, Stocks, Currencies, Materials y Strategy. Busca datos frescos de internet en cada ejecución, adapta recomendaciones al perfil de riesgo del usuario (conservador/moderado/agresivo), rastrea precisión histórica de predicciones y genera un reporte HTML interactivo bilingüe (ES/EN) servido en `localhost:3420`. Toda la información financiera permanece en la máquina del usuario. No es asesoría financiera profesional.

## Security Analysis

- **Rating**: caution
- **Allowed Tools**: WebSearch, WebFetch, Agent, Bash, Write, Read, Glob
- **Findings**:
  - Usa WebSearch y WebFetch para datos financieros en tiempo real — llamadas a internet documentadas y esperadas
  - Spawna 5 subagentes en paralelo — amplía el scope de ejecución significativamente
  - Bash: inicia servidor Node.js o Python en background (`npm run dev` o `python3 -m http.server`) — proceso background esperado
  - Bash: verifica puerto disponible con `lsof -i :3420` — operación de red local segura
  - Escribe archivos únicamente en `output/` y `dashboard/public/data/` — rutas acotadas
  - Guarda histórico JSON en `output/history/` — retención de datos local
  - Sin acceso a credenciales ni API keys financieras
  - Sin exfiltración de datos — todo local
  - Descripción coincide con el comportamiento real

## Install Command

```bash
# Abrir Claude Code en la carpeta del agente
cd "C:/01. Repositorios/Agentes/maia-skill-main/maia-skill-main"
claude
# Ejecutar via skill si está instalado:
# /investment-analysis
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del SKILL.md</summary>

```markdown
Sistema multi-agente de análisis de inversiones Tododeia v2.
Archivo completo en: C:/01. Repositorios/Agentes/maia-skill-main/maia-skill-main/SKILL.md
```

</details>

## Notes

Para automatizar reportes diarios: `/loop 24h /investment-analysis`. El dashboard Next.js requiere Node.js; si no está disponible, usa fallback HTML con Python. Incluye disclaimer visible de que no es asesoría financiera profesional.
