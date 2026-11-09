---
name: evaluator-optimizer-testing
description: >-
  Ejecuta el patrón agéntico Evaluator-Optimizer para generar, ejecutar y
  optimizar tests automatizados, detectando bugs reales en el código. Úsalo
  cuando el usuario pida realizar tests, validar bugs o invoque /testing.
---

# Patrón Evaluator-Optimizer: Testing & Bug Hunting

Orquesta un bucle iterativo entre dos roles especializados (**Generator** y **Evaluator**) para crear tests válidos y descubrir bugs reales mediante ejecución verificable.

## 1. Configuración de Stack, Herramientas y Skills

Antes de iniciar el bucle, carga y aplica la configuración de entorno definida en [stack-tools.md](./references/stack-tools.md):

- **Stack & Runner:** Identifica lenguaje, framework de test y comando de cobertura.
- **Herramientas (Tools / MCP):** Terminal (`run_command` / `bash`), lector/editor de archivos y servidores MCP configurados.
- **Skills Auxiliares:** Invoca skills complementarios según el objetivo (ej. `security-audit`, `e2e-playwright`, `api-mocking`).

## 2. Flujo del Bucle (Máximo 3 Iteraciones)

1. **Análisis Inicial:** Lee el archivo o módulo objetivo (`$TARGET`).
2. **Paso A — Generación/Optimización ([generator.md](./references/generator.md)):**
   - Si es la iteración 1: Diseña casos felices, casos borde (*edge cases*) y condiciones de error.
   - Si es iteración > 1: Corrige únicamente los tests según el feedback del Evaluador.
   - **Regla estricta:** NO modifiques el código de producción para hacer pasar un test.
3. **Paso B — Evaluación Empírica ([evaluator.md](./references/evaluator.md)):**
   - Ejecuta la suite de tests en terminal y analiza salida + cobertura.
   - Emite uno de los tres veredictos:
     - `PASS`: Todos los tests pasan y cubren las ramas críticas $\rightarrow$ **Finalizar**.
     - `RETRY_TEST`: El test falló por error de sintaxis/mock/import o baja cobertura $\rightarrow$ **Volver al Paso A** con feedback exacto.
     - `BUG_FOUND`: El test es correcto pero el código de producción falla $\rightarrow$ **Detener bucle y reportar el bug**.

## 3. Formato de Salida Final

Entrega un resumen conciso:
- **Estado:** `PASS` | `BUG_FOUND` | `MAX_ITERATIONS_REACHED`
- **Tests ejecutados y cobertura alcanzada.**
- **Bugs detectados (si aplica):** Archivo, línea, causa raíz y test que lo reproduce.
