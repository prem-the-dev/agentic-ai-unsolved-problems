# Existing Open-Source Solutions for the Money-Earning Problems

> For every money-earning problem in [MONEY-EARNING.md](MONEY-EARNING.md) (P-M1…P-M9),
> there is **already a real open-source project** attacking it. This document maps
> each problem → a verified OSS solution, with live star counts (captured
> 2026-08-04 via agent-reach: GitHub `gh` + web/Jina Reader).
>
> **Key insight:** the primitives exist. The gap is **integration** — these are 9
> separate tools, not one coherent "money-earning agent stack." Wiring them together
> (with opinionated defaults) is itself the buildable opportunity. And existence ≠
> a business: star count is not income (see the autopsy corner in
> [MONEY-EARNING.md](MONEY-EARNING.md)).

---

## The mapping

| Problem | Existing OSS solution | Stars (2026-08-04) | What it solves |
|---------|----------------------|--------------------|----------------|
| **P-M1** Distribution bottleneck | [`brightdata/ai-sdr-bdr-agent`](https://github.com/brightdata/ai-sdr-bdr-agent) (lead discovery, trigger detection, personalized outreach, CRM) + [`ZeroGTM`](https://man0l.github.io/zero-gtm/) | 11★ / — | Agent does lead-gen + DM outreach autonomously — the "find paying customers" gap |
| **P-M2** Cost vs revenue uncertainty | [`omnilabs-ai/OmniRouter`](https://github.com/omnilabs-ai/OmniRouter) (the reference router) + [`BlockRunAI/ClawRouter`](https://github.com/BlockRunAI/ClawRouter) (cuts API cost up to 87%, x402 USDC micro-pay, no API keys) + [`open-free-llm-api/awesome-freellm-apis`](https://github.com/open-free-llm-api/awesome-freellm-apis) (134+ free LLM APIs) | 30★ / — / — | Routes to the cheapest capable model; removes the per-token bill |
| **P-M3** Outcome verification / eval | [`langfuse/langfuse`](https://github.com/langfuse/langfuse) + [`Arize-ai/phoenix`](https://github.com/Arize-ai/phoenix) | 32k★ / 11k★ | Proves a task completed; agentic evals + execution traces |
| **P-M4** Agent-to-agent payment rails | [`presidio-v/presidio-hardened-x402`](https://github.com/presidio-v/presidio-hardened-x402) + [`theMobiusStrip/agentpay-guard`](https://github.com/theMobiusStrip/agentpay-guard) + [`tojunetwork/afara`](https://github.com/tojunetwork/afara) (all x402-based) | 15★ / 2★ / 9★ | USDC-paid agent commerce; spend guards + replay protection |
| **P-M5** Autonomous market-fit / validation | [`melisasvr/Autonomous-Market-Research-Agent`](https://github.com/melisasvr/Autonomous-Market-Research-Agent) + [`chankrisnachea/ai.validation.agents`](https://github.com/chankrisnachea/ai.validation.agents) | — / — | Agent researches demand + validates before building |
| **P-M6** Reliability for paid SLAs | [`agentcontrol/agent-control`](https://github.com/agentcontrol/agent-control) + [`NVIDIA-NeMo/Guardrails`](https://github.com/NVIDIA-NeMo/Guardrails) | 289★ / 6.9k★ | Centralized runtime guardrails; block injection/PII; finish-line gates |
| **P-M7** Token-cost multiplier | [`BerriAI/litellm`](https://github.com/BerriAI/litellm) (100+ LLM APIs, cost tracking, load-balancing, logging) | 55k★ | Single gateway tracks + caps spend per task |
| **P-M8** Merchant / activation gap | [`MentionNetwork/awesome-agentic-commerce`](https://github.com/MentionNetwork/awesome-agentic-commerce) + [`antoineschaller/shopify-mcp-server`](https://github.com/antoineschaller/shopify-mcp-server) (22 tools) | — / — | Pre-built agent↔commerce connectors so agents can actually sell |
| **P-M9** Agent identity & liability | [`erc-8004/erc-8004-contracts`](https://github.com/erc-8004/erc-8004-contracts) (the draft Ethereum standard) + [`sudeepb02/awesome-erc8004`](https://github.com/sudeepb02/awesome-erc8004) | 227★ / — | On-chain agent identity + reputation + validation registries |

---

## What this means

1. **The primitives exist.** For each of the 9 money-earning problems, someone has
   already open-sourced a building block. Nobody needs to invent the primitive.

2. **But most are early/small.** P-M1 (11★), P-M4 x402 guards (2–15★), P-M9 (227★)
   are real but immature. The mature ones (litellm 55k★, langfuse 32k★, NeMo 6.9k★)
   are the eval/cost/reliability layer — not the money layer.

3. **The integration layer is missing.** These are 9 separate tools, not one
   coherent pipeline. Wiring `litellm` (P-M7) + `agent-control` (P-M6) +
   `ai-sdr-bdr-agent` (P-M1) + x402 (P-M4) + `erc-8004` (P-M9) into one working
   "money-earning agent" is **unsolved** — and that integration is a buildable
   opportunity in itself (opinionated defaults + a reference architecture).

4. **Existence ≠ a business.** As the autopsy corner of
   [MONEY-EARNING.md](MONEY-EARNING.md) showed, 92% of AI side-projects fail
   (developer built 12, 8 made $0, 1 profitable). Having the tools does not create
   demand. The only problem above that points at *revenue* is P-M1 (distribution) —
   and even that needs a human-owned business around it.

---

## The real opportunity

Not "build another primitive" (done 9× over). It is one of:

- **A composable reference stack** — wire these 9 OSS projects into one agent that
  can (a) find customers (P-M1), (b) do the work cheaply via free/cheap models
  (P-M2/P-M7), (c) prove completion (P-M3), (d) get paid via x402 (P-M4), (e) stay
  identifiable + reliable (P-M6/P-M9), (f) sell through real merchant connectors
  (P-M8), (g) validate demand first (P-M5). Integration + defaults = the gap.
- **Power a human-owned service** — use these tools to run an AI SDR / automation
  agency (you own distribution; the agent is labor). This is the proven path from
  the analysis, not the "autonomous agent earns" fantasy.

---

## See also

- [MONEY-EARNING.md](MONEY-EARNING.md) — the 9 problems (P-M1…P-M9) and the honest verdict
- [PROBLEMS.md](PROBLEMS.md) — the 13 trust/reliability problems (P1–P13)
- [README.md](README.md) — full index
- [REFERENCES.md](REFERENCES.md) — source links

## Method note

Verified 2026-08-04 via agent-reach: GitHub `gh` API (authed prem-the-dev) for
star counts + repo descriptions, and web search via Jina Reader for projects that
GitHub search rate-limited. Star counts are point-in-time and decay; re-verify
before relying on any single number.
