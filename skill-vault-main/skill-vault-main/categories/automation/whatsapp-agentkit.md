---
name: whatsapp-agentkit
source_url: https://www.tododeia.com/community/whatsapp-agentkit
source_type: github
category: automation
safety_rating: caution
date_added: 2026-04-16
version: 1.0.0
tags: [whatsapp, chatbot, automation, fastapi, python, docker, webhook, business]
---

# WhatsApp AgentKit

## Description

Constructor guiado de agentes de WhatsApp con IA. Conduce al usuario por 5 fases: verificación de entorno, entrevista del negocio (10 preguntas), generación del código completo (FastAPI + Claude API + SQLite + proveedor WhatsApp), testing local en terminal y deploy a Railway. Soporta tres proveedores: Whapi.cloud (recomendado), Meta Cloud API y Twilio. Genera un agente con memoria de conversación por número de teléfono y system prompt personalizado al negocio. Todo el código se genera comentado en español.

## Security Analysis

- **Rating**: caution
- **Allowed Tools**: Bash, Read, Write, Edit (implícito via CLAUDE.md)
- **Findings**:
  - Bash: ejecuta `pip install -r requirements.txt`, `uvicorn`, `docker compose` — instalación de dependencias documentada y esperada
  - Bash: ejecuta `python tests/test_local.py` — test local controlado
  - Escribe API keys del usuario en `.env` local (NUNCA a GitHub — instrucción explícita en el agente)
  - `.gitignore` generado excluye `.env` — protección de credenciales correcta
  - Escribe código únicamente en el directorio del proyecto — rutas acotadas
  - Sin envío de datos a servidores externos durante la construcción
  - Las llamadas de red en el agente generado son a WhatsApp APIs (documentadas)
  - Sin obfuscación
  - Descripción coincide con el comportamiento real
  - Riesgo moderado: maneja API keys del usuario. Verificar que `.env` no se sube al repo.

## Install Command

```bash
# Abrir Claude Code en la carpeta del agente
cd "C:/01. Repositorios/Agentes/whatsapp-agentkit-main/whatsapp-agentkit-main"
claude
# El asistente AgentKit inicia automáticamente el onboarding
```

## Original SKILL.md Content

<details>
<summary>Ver contenido original del CLAUDE.md</summary>

```markdown
AgentKit — constructor de agentes WhatsApp con IA. 5 fases de onboarding.
Archivo completo en: C:/01. Repositorios/Agentes/whatsapp-agentkit-main/whatsapp-agentkit-main/CLAUDE.md
```

</details>

## Notes

Requiere Python 3.11+, pip y Docker para el deploy. Para pruebas sin WhatsApp real, usar `python tests/test_local.py` con tokens temporales. El deploy en Railway es gratuito en tier básico.
