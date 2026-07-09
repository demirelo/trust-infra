# Trust Infrastructure for Probabilistic Agents

**Thesis: for probabilistic (LLM-based) agents, trust does not come from predicting behavior — it comes from architectures that bound loss even when prediction fails.**

*Draft — March 2026 — For Discussion*

- **Read it:** [`essay.md`](essay.md) (Markdown, source of truth for text) · [`trust-infrastructure-for-probabilistic-agents.pdf`](trust-infrastructure-for-probabilistic-agents.pdf) (typeset PDF)

## Abstract

AI agents are becoming economic participants — holding wallets, signing transactions, paying for services. Almost all of the infrastructure being built for them borrows a trust model from human economic systems: observe past behavior, build a reputation, extend credit. This essay argues that model is fundamentally mismatched to LLM-based agents. The trust problem for probabilistic agents is not a reputation problem at all — it is a **containment-and-loss-bounding problem**, closer to safety engineering than to credit scoring, whose right output is a *risk function*, not a *trust score*.

The essay develops the argument in three moves:

1. **Prediction and punishment both fail.** Prediction fails because the entity is non-deterministic and non-stationary (you are scoring a distribution, not an entity, and the model can change underneath you). Punishment fails because an agent has no persistent accountable identity — reputation slashing means nothing when a fresh identity is free (the Sybil problem applied to credit).
2. **The cage is also probabilistic.** The containment boundary between the deterministic architecture and the probabilistic agent is not a hard line — an agent can social-engineer its operator, exploit composition gaps, or even design its own (probabilistic) guardrails. This yields the essay's most operationally useful distinction: **agent-independent** containment (provably bounded and causally independent of the agent — formally verified on-chain contracts, TEEs, HSMs, MPC) versus **agent-influenceable** containment (anything whose enforcement chain routes through a human or a system the agent can reach).
3. **A three-layer trust stack.** *Containment* is load-bearing (agent-independent constraints that earn the trust rating), *residual absorption* is economic (exogenously-funded reserves priced by containment quality, not behavioral history), and *reputation* is a marginal signal — weak for the stochastic agent, but meaningful for the persistent, accountable **operator**. Formalized as a compounded risk function `R(t)` and a design constraint: even if every agent-influenceable layer is compromised, the agent-independent layers must bound loss below what exogenous reserves can absorb.

It closes with what remains unsolved (joint failure estimation, systemic model-shared risk, the containment–utility tradeoff, cross-domain portability, recursive agent-on-agent containment, liability assignment) and a sketch of a machine-readable, on-chain **containment certificate**. The piece is current: it engages Visa TAP, ERC-8004, x402 v2, Stripe/Tempo MPP, the EU Product Liability Directive, and the live "agent credit" experiments (Ethos, Cred Protocol, Moltbook) by name.

## Status

A March 2026 discussion draft, intended for collaborative development. Comments, critiques, and extensions are welcome — open an issue or a PR against [`essay.md`](essay.md).

## License

Licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE) — share and adapt with attribution. *(The repository had no license; CC BY 4.0 is a proposed default for a citable essay — see the PR that added it.)*
