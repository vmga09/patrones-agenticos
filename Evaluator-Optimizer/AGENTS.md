# Reglas Agénticas del Proyecto (AGENTS.md)

## Testing y Detección de Bugs (Patrón Evaluator-Optimizer)

Siempre que el usuario solicite **realizar tests**, **verificar si hay bugs** o invoque el comando `/testing`:

1. **Activa el Skill:** Lee y sigue estrictamente `.agents/skills/evaluator-optimizer-testing/SKILL.md`.
2. **Carga el Stack y Herramientas:** Consulta `.agents/skills/evaluator-optimizer-testing/references/stack-tools.md` para usar el test runner, MCPs y skills auxiliares correctos.
3. **Ejecuta el Bucle Evaluator-Optimizer:**
   - Alterna entre el rol **Generator** (`references/generator.md`) y el rol **Evaluator** (`references/evaluator.md`) hasta un máximo de 3 iteraciones.
   - Si tu entorno soporta subagentes (`invoke_subagent` en AGY CLI, `Task` en Claude Code, o subagentes en OpenCode), delega la evaluación en un subagente limpio para evitar sesgo de confirmación.
4. **Inmutabilidad del Código de Producción:** Durante la fase de testing, queda prohibido modificar el código fuente productivo para forzar que un test pase. Si el test expone un fallo real, repórtalo como `BUG_FOUND`.
