### Brayner Jaime · AI QA & Automation Engineer · Colombia (UTC-5)

I build LLM agents and automations, and I measure whether they can be trusted before they ship: baselines first, acceptance thresholds, human review for the hard cases, and a regression gate so nothing gets worse silently.

| Project | What it shows | Measured |
|---|---|---|
| [caos-agent-harness](https://gitlab.com/braynerssj26/caos-agent-harness) | The harness I run my agents with: task board with atomic claims, policy guard, router by cost of error, memory over MCP, two engines (own loop and LangGraph), human review and traces | 133 tests; 26/26 injected faults caught by the test suite; the router sends critical tasks to a person because no measured system reaches the threshold |
| [agent-mcp-harness](https://gitlab.com/braynerssj26/agent-mcp-harness) | Unattended agent over MCP: tool guard, budgets, citations checked against tool output | 3B model 8/20 vs 18/20 for plain retrieval; the threshold took out-of-scope abstention from 2/4 to 4/4 |
| [ai-validation-harness](https://gitlab.com/braynerssj26/ai-validation-harness) | Validation bench: golden data, retries, review queue, regression gate | Tests catch 11/11 injected faults; 3 local models compared with confidence intervals |
| [caos-cerebro](https://gitlab.com/braynerssj26/caos-cerebro) | Knowledge base with hybrid search behind MCP and FastAPI | 89 % top-1 and 99 % top-3 on 188 questions |
| [crypto-bot](https://gitlab.com/braynerssj26/crypto-bot) | QA of a trading bot | 177 pytest tests, 83 % coverage, 15 bug reports |

Python · pytest · FastAPI · MCP · LangGraph · n8n · Ollama · Docker · GitLab CI

The code lives on GitLab (the links above); this GitHub account mirrors the profile. Every project above is my own, runs with test data, and states its scope in the README.
[LinkedIn](https://linkedin.com/in/brayner-jaime) · braynerssj26@gmail.com
