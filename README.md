### Brayner Jaime · AI Automation & QA Engineer

I design and build AI automation systems, and I test them until I can say how far they can be trusted. My work covers the whole path: the workflow or agent, the rules that limit what it can do, the tests and evaluations that measure it, and the review step where a person decides.

**How I work.** I measure a simple baseline before trusting an agent, set acceptance thresholds before running anything, send uncertain cases to human review, and keep a regression gate so nothing gets worse without notice.

**CAOS** is my AI research lab and studio. The lab side measures models and agents on real tasks and publishes the results, including the ones that went against my expectations. The studio side turns what holds up into working systems: n8n workflows, agents over MCP and the tooling to run them.

| Project | What it is | Highlight |
|---|---|---|
| [caos-agent-harness](https://gitlab.com/braynerssj26/caos-agent-harness) | A task board and policy layer for running AI agents you can check: review queue, tool guard, model router and one trace for every step | 400+ tests · 26/26 injected faults caught |
| [agent-mcp-harness](https://gitlab.com/braynerssj26/agent-mcp-harness) | An unattended agent over MCP with a tool guard, budgets and citations checked against tool output | 8/20 vs 18/20 against plain retrieval |
| [ai-validation-harness](https://gitlab.com/braynerssj26/ai-validation-harness) | A validation bench: golden data, retries, review queue and a regression gate | 11/11 injected faults caught |
| [caos-cerebro](https://gitlab.com/braynerssj26/caos-cerebro) | A knowledge base with hybrid search behind MCP and FastAPI | 89 % top-1 · 99 % top-3 on 188 questions |
| [Caos CryptoQA](https://gitlab.com/braynerssj26/crypto-bot) | A QA case study on an async Solana data and execution pipeline | 177 tests · 83 % coverage · 15 bug reports |

Python · pytest · FastAPI · MCP · LangGraph · n8n · Ollama · Docker · GitLab CI

braynerssj26@gmail.com · [LinkedIn](https://linkedin.com/in/brayner-jaime) · Colombia, remote
