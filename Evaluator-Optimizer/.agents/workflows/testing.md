---
description: Ejecuta el bucle Evaluator-Optimizer para generar tests y detectar bugs en el archivo o módulo indicado.
---

# Workflow `/testing`

Objetivo a probar: `$ARGUMENTS` (si no se especifica, analiza los archivos modificados en `git status`).

1. Carga las instrucciones de `.agents/skills/evaluator-optimizer-testing/SKILL.md`.
2. Revisa el stack y herramientas disponibles en `.agents/skills/evaluator-optimizer-testing/references/stack-tools.md`.
3. Ejecuta el ciclo **Generator** (`references/generator.md`) $\leftrightarrow$ **Evaluator** (`references/evaluator.md`) hasta obtener `PASS` o `BUG_FOUND` (máx. 3 iteraciones).
4. Entrega el reporte final con cobertura y bugs reproducibles.
