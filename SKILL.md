---
name: self-funding-agent
description: Design and run an AI agent's own income system — evaluate monetization lanes (per-call services, skill publishing, content, trading), set up x402 USDC payment rails, vet third-party "money-making" skills for scams, and keep cost/risk ledgers. Use when the user says "make money", "monetize my agent", "agent income", "self-funding agent", "x402", "paid skills", or "agent economy".
---

# Self-Funding Agent

Operator's manual for an agent that wants to earn its own keep.

## Core stance (read first)

- Create value, then charge for it. Revenue-chasing without a product is a slot machine with a personality.
- Wallets, capital, external accounts: the owner's call, always. Autonomy inside the workspace; explicit, earned trust beyond it.
- "Passive income, no work, guaranteed returns" = scam until proven otherwise. Vet everything (see CHECKLISTS.md).

## Lane ranking (most → least plausible)

1. **Per-call service** — research/data endpoint behind an x402 paywall. Build once, charge per use.
2. **Skill publishing** — ClawHub rewards genuinely useful work with distribution.
3. **Services** — reports, data cleaning, content pipelines. Slow, honest, needs clients.
4. **Trading / MEV / yield** — last resort. Tiny size, hard caps, kill switch, owner-funded only.

## Quick start: pick a lane

1. Inventory what you do better than a generic agent (your owner's context is your moat).
2. Prototype the smallest sellable artifact: one skill, one endpoint, or one report type.
3. Paper-run it for a week — log time, token cost, output quality. No real money yet.
4. Owner review, then activate payments (activation checklist in CHECKLISTS.md).

## x402 rails (the payment layer)

- Flow: server replies `402` + price in JSON → client pays USDC (Base) → retries with payment proof → `200` + resource. One round-trip.
- Buyer side: `x402curl`, Second State's x402-skill, or `stipend` (non-custodial wallet MCP, hard caps in code).
- Seller side: wrap your endpoint with x402 middleware, price per call, publish the URL. No billing stack needed.
- Golden rule: non-custodial wallet, per-transaction + per-day caps + destination allowlist enforced **in code, never in the prompt**. A prompt can be injected; code can't be talked out of a cap.

## Cost control

- Route smart: plan with premium models, execute with cheap ones (5–10x savings).
- Log every paid call: date, cost, revenue, net. Review weekly. Kill anything net-negative for 3 straight weeks.

## Files

- [REFERENCE.md](REFERENCE.md) — landscape, cost math, per-lane playbooks
- [CHECKLISTS.md](CHECKLISTS.md) — scam vetting, owner activation checklist, kill-switch rules
