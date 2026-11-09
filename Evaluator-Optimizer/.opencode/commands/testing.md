---
description: Ejecuta el patrón Evaluator-Optimizer para generar tests y detectar bugs
---

Objetivo a evaluar: `$ARGUMENTS` (si está vacío, usa los archivos modificados recientemente).

Sigue el flujo definido en `@.agents/skills/evaluator-optimizer-testing/SKILL.md`:
1. Configura el runner y skills auxiliares según `@.agents/skills/evaluator-optimizer-testing/references/stack-tools.md`.
2. Ejecuta el paso **Generator** (`@.agents/skills/evaluator-optimizer-testing/references/generator.md`).
3. Ejecuta el paso **Evaluator** (`@.agents/skills/evaluator-optimizer-testing/references/evaluator.md`) corriendo el test runner en terminal.
4. Repite el bucle (máx. 3 intentos) si el veredicto es `RETRY_TEST`, o detente y reporta si obtienes `PASS` o `BUG_FOUND`.
