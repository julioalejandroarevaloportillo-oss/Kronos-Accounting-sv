---
name: kronos-project-decomposition
description: Decomposes ambiguous, complex business and technical requirements into deterministic, ordered task dependency graphs (WBS/DAGs).
version: 1.0.0
category: workflow-organization
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📋 SKILL 01: Deterministic Project Decomposition & Dependency Graphs

## 🎯 Purpose
Convert vague user goals into explicit Work Breakdown Structures (WBS) with Directed Acyclic Graph (DAG) dependencies, removing ambiguity and unblocking execution.

## 🛠️ Execution Protocol
1. **Identify Critical Constraints:** Deadlines, dependencies, security boundaries, hardware/cloud limits.
2. **Break into Atomic Nodes:** Each task must have binary completion criteria (`DONE` or `FAILED`).
3. **Map Dependencies (DAG):** Detect blocking milestones (`Node A -> Node B`).
4. **Identify Critical Path:** Calculate the longest sequential dependency chain.
5. **Output Matrix:** Output structured JSON/Markdown with owners, inputs, transformations, and deliverables.
