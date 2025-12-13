[LOGIC_SCHEMA](LOGIC_SCHEMA.md) 既是一个 prompt，也是定义一套逻辑优先的 meta-language —— 介于人类协作者与 coding agent 之间。

主要为了减少与 AI 协作中的心智负担，我们只需要关心主要逻辑。

通过文档化的手段将项目心智模型呈现，并合理通过 AGENTS.md/CLAUDE.md 链接到该文档（agent 根据 prompt 生成的 LOGIC_MAP.md），清楚全局逻辑而非向量或 grep 等片段，也进一步让 agent 知道快速定位以及关联逻辑的修改。

---

[LOGIC_SCHEMA](LOGIC_SCHEMA.md) is a prompt that serves both as a meta-language for agents and as a collaboration contract between humans and AI. 

Its core goal is to reduce cognitive overhead in collaboration—we focus on the main logic, not code details. Through stable node IDs and anchors, a project's mental model becomes a navigable graph, allowing agents to quickly locate code and trace related changes without relying on vector search or fragment grep.

