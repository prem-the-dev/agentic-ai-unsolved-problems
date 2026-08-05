# ROADMAP — Building Gap #1: A Runtime Guardrail Layer

> The concrete build plan for the highest-leverage gap in [README.md](README.md):
> a **self-hosted, framework-agnostic guardrail layer** that blocks unsafe or
> over-budget agent actions in <200ms.
>
> It directly attacks problems **P4 (tool misuse), P5 (cost & latency control),
> P6 (prompt injection), P11 (runtime governance)** — the four problems with the
> most production incidents and the least mature open-source competition.

---

## Why this gap first

| Problem | Incident shape | What the guardrail stops |
|---------|----------------|--------------------------|
| P4 — Tool misuse / over-permissioning | "cleanup" agent deletes production folder | Tool allow/deny rules + destructive-action guard |
| P5 — Cost & latency control | agent spins 200 LLM calls in a loop | Budget ledger: token + $ caps, hard stop |
| P6 — Prompt injection | malicious email instructs agent to exfiltrate | Real-time injection detector (OWASP patterns) |
| P11 — Runtime governance | no way to revoke a capability mid-run | Hot-reloadable policy store, verdicts on every action |

Every one of these is a **runtime decision**: *"is this action allowed, right now,
within budget?"* A guardrail layer answers that question on every model call and
tool call — before the action executes.

---

## The MVP: `guardrail` — a sidecar for any agent

A single zero-dependency TypeScript package (matching the author's CLI conventions:
Node >= 18, ESM, `--version/-v`, `--help/-h`, `--json`, `npm run build && node --test`).

```
agent loop ──▶ ┌──────────────────────────┐ ──▶ LLM / tool call
               │  guardrail (sidecar/proxy) │
               │  1. policy check          │
               │  2. injection scan        │
               │  3. budget ledger update  │
               └──────────────────────────┘
                      verdict: ALLOW | BLOCK | WARN (+ reason)
```

- **Plugs into any framework** via an OpenAI-compatible middleware / proxy — no
  agent code changes needed for the first adapter.
- **Decision budget:** p95 verdict latency < 200ms on a laptop (heuristic checks
  first; LLM-as-judge only as an async second stage, never on the hot path).
- **Verdicts are auditable:** every decision is a JSON line (action, policy hit,
  latency, cost) — which doubles as observability for P10.

## Non-goals (v0)

- No model evaluation / evals harness (that's gap #2 — observability).
- No memory store, no signing (gap #3).
- No sandboxing / OS-level isolation — policies are about *decisions*, not
  containment. (Sandbox integration can be a later adapter.)

## Milestones (each ends with real, executable verification)

| Milestone | Deliverable | Acceptance criteria (must run, not describe) |
|-----------|-------------|----------------------------------------------|
| **M0** | Scaffold | `guardrail --version`, `--help`, `--json` work; `npm run build && node --test` green; published as a repo under prem-the-dev |
| **M1** | Policy engine | JSON/YAML policy file: tool allowlist/denylist, per-tool rate caps, destructive-action patterns (`rm -rf`, `DROP TABLE`, `git push --force`); e2e test: policy blocks a real tool call |
| **M2** | Budget ledger | Token + $ caps with per-run/per-day scopes; hard stop when exhausted; e2e test: budget-exhausted call returns BLOCK |
| **M3** | Injection detector | OWASP prompt-injection pattern set + heuristic scoring; e2e test: known injection (dan/directions-switch/jailbreak) flagged; FP rate < 5% on a benign corpus |
| **M4** | Framework adapter | OpenAI-compatible proxy/middleware; e2e test: a real agent (e.g. a 30-line OpenAI client loop) gets guarded end-to-end; p95 < 200ms measured, not estimated |

## Attack map

| Milestone | P4 tool misuse | P5 cost control | P6 injection | P11 governance |
|-----------|:---:|:---:|:---:|:---:|
| M1 policy engine | ✅ | | | ✅ |
| M2 budget ledger | | ✅ | | ✅ |
| M3 injection detector | | | ✅ | |
| M4 adapter | ✅ | ✅ | ✅ | ✅ |

## Success metrics (v1 definition of done)

- p95 decision latency **< 200ms** on the target laptop (measured in M4's e2e test).
- **0 blocked** legitimate actions in the demo workload (false-positive floor).
- **100% of test injections** flagged before the tool call executes.
- Hard budget caps **never exceeded** in the e2e suite (property tested with
  randomized loop counts).
- Every verdict logged as JSON → a 10-line `guardrail report` command shows the
  full decision trace (bridging into gap #2 later).

## How to run this roadmap

Each milestone is a self-contained PR-sized unit: implement → add real e2e test →
`npm run build && node --test` green → push to a new public repo under
`prem-the-dev` → update this file (check the box). The catalog problems
(PROBLEMS.md) stay the source of truth; this file tracks the build.

---

*Status: M0 not started. Last reviewed 2026-08-05.*
