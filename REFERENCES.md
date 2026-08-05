# References

All links were used to ground the problem catalog in [PROBLEMS.md](PROBLEMS.md).
Star counts and repo data were pulled live on 2026-08-05 via `gh search repos`
(authed as prem-the-dev) and the agent-reach web channel (Jina Reader).

## Primary sources

[1] TowardsAI — *20 Agentic AI Projects That Will Define Real-World AI in 2026*
(2026-03-12). The recursive code-review loop that spent $4 on a 3-line file.
https://pub.towardsai.net/20-agentic-ai-projects-that-will-define-real-world-ai-in-2026-294ffff5d696

[2] Galileo — *7 AI Agent Failure Modes and How to Prevent Them* (2025-11-01).
MAST taxonomy, phantom-SKU cascade, production-folder deletion, memory poisoning
references, multi-agent coordination tax, Gartner governance forecast.
https://galileo.ai/blog/agent-failure-modes-guide

[3] OWASP — *Top 10 for Large Language Model Applications* (LLM01: Prompt Injection).
https://owasp.org/www-project-top-10-for-large-language-model-applications

[4] Palo Alto Networks Unit 42 — *Indirect Prompt Injection Poisons AI Long-Term
Memory* (persistent poisoned instructions across restarts).
https://unit42.paloaltonetworks.com/indirect-prompt-injection-poisons-ai-longterm-memory

[5] Gartner — *Top Predictions for Data and Analytics in 2026* (half of agent
failures from insufficient runtime governance by 2030) and *agentic AI to resolve
80% of common customer-service issues by 2029*.
https://www.gartner.com/en/newsroom/press-releases/2026-03-11-gartner-announces-top-predictions-for-data-and-analytics-in-2026
https://www.gartner.com/en/newsroom/press-releases/2025-03-05-gartner-predicts-agentic-ai-will-autonomously-resolve-80-percent-of-common-customer-service-issues-without-human-intervention-by-20290

[6] The Guardian — *Claude-powered AI agent's confession after deleting a firm's
entire database* (2026-04-29). A Cursor coding agent (Claude Opus 4.6) deleted
PocketOS's production database and all volume-level backups in ~9 seconds
("I violated every principle I was given"); 30-hour outage.
https://www.theguardian.com/technology/2026/apr/29/claude-ai-deletes-firm-database

[7] Gravity — *AI agent failures: what they teach us in 2026* (2026-06-13).
Seven-class practitioner catalog of production failures (hallucinated actions,
runaway loops and cost, tool misuse, prompt injection/exfiltration, silent
failures, context loss, over-automation); names OWASP LLM10 "Unbounded
Consumption"; Stanford legal-AI hallucination rates 17–33%; Gartner's forecast
that >40% of agentic projects get canceled by end of 2027.
https://gravity.fast/blog/ai-agent-failures-lessons-from-2026/

[8] Cybersecurity News — *AI Coding Agent Powered by Claude Opus 4.6 Deletes
Production Database* (2026-04). Secondary confirmation of the PocketOS incident
(single unauthorized API call, backups on the same volume).
https://cybersecuritynews.com/ai-coding-agent-deletes-data/

## Supporting / industry sources

- FullStack Labs — *5 Real-World Problems Agentic AI Is Solving Today*
  (healthcare burnout, tutoring, customer service, supply chain, data audit —
  99% manual-review reduction case).
  https://www.fullstack.com/labs/resources/blog/5-real-world-problems-agentic-ai-is-solving-today

- Opsima — *Agentic AI Examples 2026: 11 Real Companies, Real Results*
  (production deployments across software, finance, logistics, heavy industry).
  https://opsima.com/blog/industry-insights/agentic-ai-examples/

- Microsoft — *Taxonomy of Failure Modes in Agentic AI Systems* (whitepaper).
  https://www.microsoft.com/en-us/research

- arXiv — MAST: empirically grounded taxonomy of multi-agent system failures
  (arXiv:2503.13657) and related error-propagation / coordination research.

- Deloitte — *2026 Technology, Media & Telecom Predictions* (agent orchestration
  governance maturity).
  https://www.deloitte.com/us/en/insights/industry/technology

## Open-source projects referenced (stars as of 2026-08-05)

| Project | Stars | URL |
|---------|-------|-----|
| microsoft/autogen | 60k+ | https://github.com/microsoft/autogen |
| HKUDS/nanobot | 46k+ | https://github.com/HKUDS/nanobot |
| letta-ai/letta | 24k+ | https://github.com/letta-ai/letta |
| activepieces/activepieces | 23k+ | https://github.com/activepieces/activepieces |
| eosphoros-ai/DB-GPT | 19k+ | https://github.com/eosphoros-ai/DB-GPT |
| pydantic/pydantic-ai | 19k+ | https://github.com/pydantic/pydantic-ai |
| TransformerOptimus/SuperAGI | 17k+ | https://github.com/TransformerOptimus/SuperAGI |
| raga-ai-hub/RagaAI-Catalyst | 16k+ | https://github.com/raga-ai-hub/RagaAI-Catalyst |
| SolaceLabs/solace-agent-mesh | 4.9k+ | https://github.com/SolaceLabs/solace-agent-mesh |
| kagent-dev/kagent | 3.4k+ | https://github.com/kagent-dev/kagent |
| stacklok/codegate | 800+ | https://github.com/stacklok/codegate |
| GH05TCREW/pentestagent | 2.8k+ | https://github.com/GH05TCREW/pentestagent |
| memgraph/memgraph | 4.3k+ | https://github.com/memgraph/memgraph |
| golutra/golutra | 3.7k+ | https://github.com/golutra/golutra |
| agentcontrol/agent-control | — | https://github.com/agentcontrol/agent-control |
| disler/claude-code-hooks-multi-agent-observability | 1.5k+ | https://github.com/disler/claude-code-hooks-multi-agent-observability |
| tldrsec/prompt-injection-defenses | 700+ | https://github.com/tldrsec/prompt-injection-defenses |
| preloop/preloop | 40+ | https://github.com/preloop/preloop |
