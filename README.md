# Brayner — AI & workflow automation engineer

I build **self-hosted automation** (n8n · APIs · local LLMs) and hand it over **test-gated and
documented**. Every number on this page links to the place where you can check it — that is the
point of the page.

---

## What I build

**Workflow automation.** Lead capture → CRM → instant alert, scheduled reporting, document
processing. Self-hosted n8n plus a small SQLite CRM, run as `systemd --user` services: an
open-source stack with no license fees, and the data never leaves the client's machine.

**AI where it actually pays off.** Local LLMs (Qwen3 via Ollama / LM Studio) for classification,
extraction and scoring — the cases where data has to stay private or per-call cost matters.

**QA on top of both.** pytest suites, coverage gates, and bug reports with root-cause analysis.
This is the part automation work usually skips, and it is why a handover of mine still holds after
I leave.

---

## Public work

### [`caos-stack`](https://gitlab.com/braynerssj26/caos-stack) — self-hosted automation backend · GitLab

n8n 2.8.4 (npm) and a minimal SQLite CRM, wired as user-level `systemd` services bound to
loopback. The repo ships what makes it reproducible, not a description of it:

- [`n8n-studio/workflows/lead-capture-v1.json`](https://gitlab.com/braynerssj26/caos-stack/-/blob/main/n8n-studio/workflows/lead-capture-v1.json)
  — the lead-capture pipeline, exported: `Webhook → CRM → ntfy → Telegram`
- [`systemd/`](https://gitlab.com/braynerssj26/caos-stack/-/tree/main/systemd) +
  [`scripts/install-systemd.sh`](https://gitlab.com/braynerssj26/caos-stack/-/blob/main/scripts/install-systemd.sh)
  — the units and their installer
- [`docs/SETUP.md`](https://gitlab.com/braynerssj26/caos-stack/-/blob/main/docs/SETUP.md) ·
  [`docs/ARQUITECTURA.md`](https://gitlab.com/braynerssj26/caos-stack/-/blob/main/docs/ARQUITECTURA.md) ·
  [`docs/TROUBLESHOOTING.md`](https://gitlab.com/braynerssj26/caos-stack/-/blob/main/docs/TROUBLESHOOTING.md)
  — setup, the design decisions, and the failures that cost me hours (systemd does not expand
  `$HOME` in `EnvironmentFile=`; n8n 2.x registers the production webhook under the workflow id,
  not the path you typed)

Verified on Linux Mint 22.3 / Ubuntu 24.04 · Python 3.12 · Node 20. Docs in Spanish.

### [`Crypto.Bot`](https://github.com/caos-ssj/Crypto.Bot) — Solana trading bot, and the QA system around it · Python

Full pipeline: detection (DexScreener) → on-chain analysis (Helius) → 11 weighted filters → local
AI scoring (Qwen3) → decision → swap execution (Jupiter), with TP/SL/trailing risk management and
a Streamlit dashboard. **`DRY_RUN` by default** · GPL-3.0.

Scoring rule of the project: if an on-chain fact cannot be verified, it scores **0** — a token is
never assumed safe just because the data is missing.

The QA work on it is what I actually show clients —
[`docs/QA-CASE-STUDY.md`](https://github.com/caos-ssj/Crypto.Bot/blob/main/docs/QA-CASE-STUDY.md):

| Result | Where to check it |
|---|---|
| **176 `pytest` tests**, up from 130 | [`tests/`](https://github.com/caos-ssj/Crypto.Bot/tree/main/tests) |
| **83 % coverage**, up from 67 % (blocking gate: 60 %) | [`Makefile`](https://github.com/caos-ssj/Crypto.Bot/blob/main/Makefile) · [`.github/workflows/ci.yml`](https://github.com/caos-ssj/Crypto.Bot/blob/main/.github/workflows/ci.yml) |
| **15 bug reports with root-cause analysis** | [`docs/bug-reports/`](https://github.com/caos-ssj/Crypto.Bot/tree/main/docs/bug-reports) |
| Weakest modules closed first: `fetcher.py` 20 % → 94 %, `main.py` 35 % → 70 % | [`docs/QA-CASE-STUDY.md`](https://github.com/caos-ssj/Crypto.Bot/blob/main/docs/QA-CASE-STUDY.md) |

Two of those bugs were found *by writing the tests*, not by a user:
[#023](https://github.com/caos-ssj/Crypto.Bot/blob/main/docs/bug-reports/bug-023-fetcher-malformed-pair.md)
— a single malformed DexScreener pair crashed the whole token search;
[#024](https://github.com/caos-ssj/Crypto.Bot/blob/main/docs/bug-reports/bug-024-ai-lmstudio-doble-v1.md)
— a duplicated `/v1/v1` endpoint made the AI layer silently score 0 on every token. Both fixed and
covered by regression tests.

`make check` runs the same gate locally that the CI file runs: ruff + black + coverage.

---

## Toolbox

```
Automation   n8n · webhooks · REST APIs · MCP servers · SQLite · systemd · Docker · bash
AI           local LLMs (Qwen3 via Ollama / LM Studio) · OpenAI-compatible clients · JSON output contracts
QA           pytest · pytest-asyncio · coverage gates · Postman/Newman · GitHub Actions · ruff · black
Code         Python 3.12 · JavaScript · SQL
```

## How I work

- No claim without a link to where it can be checked.
- Anything touching money or production ships with a dry-run mode first.
- A delivery is not finished until its setup, architecture and failure modes are written down.

## Contact

- Email: `braynerssj26@gmail.com`
- Or open an issue / PR on any repo here.
- Spanish and English (`Crypto.Bot` is documented in both, `caos-stack` in Spanish).
