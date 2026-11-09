# Registro de Stack, Herramientas y Skills

Modifica o adapta esta sección según las tecnologías del repositorio actual.

## 1. Stack & Comandos de Ejecución

| Ecosistema | Test Runner | Comando Base | Comando Cobertura |
| :--- | :--- | :--- | :--- |
| **Node / TS** | Vitest / Jest | `npx vitest run <file>` | `npx vitest run --coverage` |
| **Python** | Pytest | `pytest <file> -v` | `pytest --cov=<module> <file>` |
| **Go** | Go Test | `go test -v ./...` | `go test -cover ./...` |
| **Rust** | Cargo | `cargo test` | `cargo tarpaulin` |
| **.NET / C#** | xUnit / NUnit | `dotnet test` | `dotnet test --collect:"XPlat Code Coverage"` |

## 2. Herramientas Requeridas (ACI / MCP)

- **Ejecución:** Terminal / Bash para correr el *test runner* y linters.
- **Archivos:** Lectura del código fuente y escritura exclusiva en archivos `*.test.*` o `*_test.*`.
- **MCP Opcionales:**
  - `playwright` / `puppeteer`: Si el objetivo requiere pruebas E2E en navegador.
  - `postgres` / `sqlite`: Si se validan queries o migraciones en entorno de prueba.

## 3. Llamada a Skills Complementarios

Activa o encadena estos skills si están disponibles en `.agents/skills/`:

- **Pre-Test (Análisis):** `code-review` o `security-check` para identificar puntos débiles antes de diseñar los casos de prueba.
- **Durante Generación:** `mock-generator` o `fixtures-builder` para datos de prueba complejos.
- **Post-Bug:** `bug-fixer` (solo si el usuario autoriza corregir el código de producción tras detectar un `BUG_FOUND`).
