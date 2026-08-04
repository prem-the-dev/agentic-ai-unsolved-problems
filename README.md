# Agentic AI — Unsolved Problems

> A living catalog of the problems that still block **useful, real-world agentic AI**.
> Frameworks are mostly solved. Reliability, safety, memory, observability, and
> governance are not. This repo documents exactly where the hard problems are,
> so you can pick a gap worth building a project around.

---

## Why this repo exists

In 2024–2026 the agentic-AI ecosystem produced a flood of **frameworks**:
AutoGen (60k★), NanoBot (46k★), Letta (24k★), Pydantic-AI (19k★), SuperAGI (17k★),
and dozens more. If you want to *build* an agent, the tooling is mature.

What is **not** solved is making agents that you can actually trust in production:

- agents that **stop** when they should,
- agents that **don't delete your production folder** because "cleanup" sounded efficient,
- agents whose **memory can't be poisoned** by a malicious email,
- agents whose **silent failures** show up on a dashboard *before* they reach a customer.

The defining engineering challenge of agentic AI is no longer "make it act."
It is **"action bounded by judgment."** This repo enumerates the open problems
behind that sentence, each grounded in real incident reports and primary sources
(see [REFERENCES.md](REFERENCES.md) and [PROBLEMS.md](PROBLEMS.md)).

---

## How to use this repo

1. Skim the **Problem index** below to see the landscape.
2. Open [PROBLEMS.md](PROBLEMS.md) for a deep entry on any problem: what it is,
   a real incident, why current solutions fall short, and what a good solution needs.
3. Use [REFERENCES.md](REFERENCES.md) to read the original sources.
4. See **Where to build** for the least-saturated, highest-leverage gaps.

---

## Problem index

| # | Cluster | Problem | Status in 2026 | Build leverage |
|---|---------|---------|----------------|----------------|
| 1 | Reliability | Knowing when to stop / runaway loops | Unsolved (no standard halt primitive) | ★★★ |
| 2 | Reliability | Verification & termination failures | Partial (manual validators only) | ★★★ |
| 3 | Reliability | Hallucination cascades | Unsolved (single fabrications → fleet incidents) | ★★★ |
| 4 | Safety | Tool misuse / over-permissioning | Partial (sandbox patterns exist, not default) | ★★★ |
| 5 | Safety | Cost & latency control at runtime | Early (LLM-as-judge too slow/expensive) | ★★★ |
| 6 | Security | Prompt injection (direct + indirect) | Open (OWASP #1, no cheap real-time detector) | ★★★ |
| 7 | Security | Memory poisoning across sessions | Early (proven PoC exists, few defenses) | ★★★ |
| 8 | Multi-agent | Communication breakdowns / coordination tax | Partial (research, little tooling) | ★★☆ |
| 9 | Design | Ambiguity gaps in specs | Open (no constraint validation standard) | ★★☆ |
| 10 | Observability | Semantic failures invisible to monitoring | Early (few agentic metrics) | ★★★ |
| 11 | Governance | Runtime governance / policy enforcement | Early (centralized hot-reload policies immature) | ★★★ |
| 12 | Memory | Memory rot / drift over time | Open (no standard versioned rollback) | ★★☆ |
| 13 | Grounding | Weak grounding / RAG quality | Partial (poisoning + staleness unsolved) | ★★☆ |

---

## Where to build (least saturated, highest leverage)

The framework space is crowded. The **open gaps with little mature open-source
competition** are:

1. **Runtime guardrails + cost control** — a self-hosted layer that plugs into
   *any* framework and blocks unsafe/over-budget actions in <200ms.
   (attacks problems 4, 5, 6, 11)
2. **Agent observability / evaluation** — agentic-specific metrics
   (Action Completion, Tool Selection Quality, Reasoning Coherence) with
   execution traces spanning multi-agent handoffs. (attacks 3, 8, 10)
3. **Memory poisoning prevention** — signed, versioned, provenance-tracked
   memory with rollback. (attacks 7, 12)
4. **Domain agents with hard verification** — healthcare / legal / compliance
   where "stopping early" is unacceptable; multi-stage validators as a primitive.
   (attacks 2, 13)

A self-hosted, framework-agnostic **guardrail + eval** layer (1) directly attacks
the most incidents and is the least-solved, most-needed piece.

---

## Related open-source to study

| Project | Stars | Relevance |
|---------|-------|-----------|
| microsoft/autogen | 60k+ | Multi-agent framework baseline |
| HKUDS/nanobot | 46k+ | Self-hosted personal agent |
| raga-ai-hub/RagaAI-Catalyst | 16k+ | Agent observability / eval (one of the few serious OSS) |
| stacklok/codegate | 800+ | Security guardrails for agent frameworks |
| kagent-dev/kagent | 3.4k+ | Cloud-native agent ops |
| GH05TCREW/pentestagent | 2.8k+ | Autonomous security testing |
| agentcontrol/agent-control | — | Centralized hot-reloadable agent policies (early-stage) |

*(Star counts captured 2026-08-04 via `gh search repos`; see research notes.)*

---

## Contributing

Found a new unsolved problem, a better reference, or a project that closes one of
these gaps? See [CONTRIBUTING.md](CONTRIBUTING.md). Keep entries grounded in a
real source or incident — no speculation without a link.

## License

MIT — see [LICENSE](LICENSE).
