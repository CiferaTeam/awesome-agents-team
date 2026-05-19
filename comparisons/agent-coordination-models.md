# Agent Coordination Models

> How do different tools coordinate multiple AI agents toward a shared goal?

This comparison covers the core coordination primitives each tool uses — how agents discover work, communicate state, and hand off to one another.

**Status**: Stub — to be populated in Phase 1.

| Dimension | Description |
|-----------|-------------|
| Coordination primitive | e.g. message bus, shared DB, Git commits, API polling |
| State visibility | Can agents see each other's state? How? |
| Conflict resolution | What happens when two agents try to write the same state? |
| Human checkpoints | Where are humans required to approve before agents proceed? |
| Async vs sync | Does coordination require agents to be online simultaneously? |

<!-- Fill in rows per product in Phase 1 -->

---

*See also: [Data ownership & portability](data-ownership.md) · [Local-first vs cloud tradeoffs](local-vs-cloud.md)*
