---
description: Ejecuta el patrón Evaluator-Optimizer para crear tests y detectar bugs reales.
argument-hint: [ruta-archivo-o-modulo]
allowed-tools: Bash, Read, Write, Edit, Glob, Grep, Task
---

Ejecuta el patrón **Evaluator-Optimizer** sobre el objetivo: `$ARGUMENTS` (o archivos modificados si está vacío).

1. Lee `.agents/skills/evaluator-optimizer-testing/SKILL.md` y `.agents/skills/evaluator-optimizer-testing/references/stack-tools.md`.
2. **Fase Generator:** Siguiendo `.agents/skills/evaluator-optimizer-testing/references/generator.md`, escribe o refina los tests cubriendo casos felices, casos borde y errores sin tocar el código productivo.
3. **Fase Evaluator:** Usa la herramienta `Bash` (o lanza un subagente con `Task`) siguiendo `.agents/skills/evaluator-optimizer-testing/references/evaluator.md` para correr los tests y emitir `PASS`, `RETRY_TEST` o `BUG_FOUND`.
4. Itera hasta un máximo de 3 veces si el veredicto es `RETRY_TEST`.
