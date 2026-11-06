---
name: kronos-first-time-right-code-spec
description: Enforces production-grade code generation with type hints, deterministic error handling, input validation, and zero placeholding.
version: 1.0.0
category: anti-slop-standards
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 🛡️ SKILL 15: Anti-Slop: First-Time-Right Code & Zero-Lazy-Placeholders

## 🎯 Purpose
Eliminate lazy AI coding habits such as `# TODO: implement this`, `// write your logic here`, unhandled exceptions, and missing type definitions.

## 🛠️ Execution Protocol
1. **Ban All Code Placeholders:** Every function, class, and method must be fully implemented, end-to-end.
2. **Type Safety & Typing:** Enforce static typing (`typing.Dict`, `typing.Optional`, Pydantic models, or TypeScript interfaces).
3. **Explicit Error Boundaries:**
   - Never write bare `except:` or `catch (e) {}`.
   - Wrap IO, network, and database operations in explicit try-catch blocks with descriptive error logs.
4. **Self-Contained Executability:** Provide full imports, environment variable references, and a working test harness or `if __name__ == "__main__":` entry point.
