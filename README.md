[LOGIC_SCHEMA](LOGIC_SCHEMA.md) 既是一个 prompt，也是定义一套逻辑优先的 meta-language —— 介于人类协作者与 coding agent 之间。

主要为了减少与 AI 协作中的心智负担，我们只需要关心主要逻辑。

通过文档化的手段将项目心智模型呈现，并合理通过 AGENTS.md/CLAUDE.md 链接到该文档（agent 根据 prompt 生成的 LOGIC_MAP.md），清楚全局逻辑而非向量或 grep 等片段，也进一步让 agent 知道快速定位以及关联逻辑的修改。

---

[LOGIC_SCHEMA](LOGIC_SCHEMA.md) is a prompt that serves both as a meta-language for agents and as a collaboration contract between humans and AI. 

Its core goal is to reduce cognitive overhead in collaboration—we focus on the main logic, not code details. Through stable node IDs and anchors, a project's mental model becomes a navigable graph, allowing agents to quickly locate code and trace related changes without relying on vector search or fragment grep.

---

Use in Claude.md/Agents.md:
```markdown
## Agent Workflow & Logic Mapping

This project uses a **logic-first mental model** approach defined in `docs/LOGIC_SCHEMA.md`. Follow this protocol for efficient codebase navigation and maintenance.

### LOGIC_MAP.md Usage

**Purpose**: `LOGIC_MAP.md` (in repo root) is a project-specific logic map that provides:
- A graph of system components, flows, and invariants
- Stable IDs for navigation (`CMP-*`, `FLOW-*`, `INV-*`)
- Direct anchors to code locations (file#SymbolPath)
- Evidence references (tests, assertions)

**Mandatory Protocol**:
1. **Always read `LOGIC_MAP.md` first** when starting work on this repository
2. **Update the map** as part of "done" for significant changes
3. **Use anchors** to navigate code rather than broad scanning

### When to Use LOGIC_MAP.md

**Scenario A (Bootstrap)**: If `LOGIC_MAP.md` doesn't exist, create it following `docs/LOGIC_SCHEMA.md` guidelines.

**Scenario B (Task-oriented exploration)**:
1. Read `LOGIC_MAP.md` as the project index
2. Convert user request to candidate nodes (`FLOW-*` for behavior, `CMP-*` for modules)
3. Traverse `relations` to find adjacent nodes
4. Follow `anchors` into code/tests/config
5. Only search broadly if map is insufficient

**Scenario C (Maintenance)**: Update map when code changes:
- Update nearest `FLOW-*` steps for behavior changes
- Add/update `REL-*` edges for new dependencies
- Update anchors for refactored symbols/files
- Add `INV-*` for new constraints with `EVD-*` evidence

### Relationship with CLAUDE.md

- **CLAUDE.md**: Always-on agent rulebook (this file) - enforces the protocol
- **LOGIC_MAP.md**: Project index (nodes + relations + anchors) - provides navigation
- **docs/LOGIC_SCHEMA.md**: Schema + methodology - defines the format

### Quick Start for Agents

1. **First action**: Check for `LOGIC_MAP.md` in repo root
2. **If exists**: Read it, identify relevant nodes, follow anchors
3. **If missing**: Create minimal map (1 system, 5-12 components, 2-5 flows)
4. **When done**: Update map if significant changes were made
```
