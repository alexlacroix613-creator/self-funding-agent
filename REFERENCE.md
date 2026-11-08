# Reference — The Agent-Income Landscape

Synthesized from ClawHub + GitHub recon (2026-11). Opinionated; verify before betting anything.

## The stack that matters

| Layer | What it does | Examples |
|---|---|---|
| Payment rail | Pay/receive per HTTP request, USDC | x402 protocol, facilitators |
| Wallet (buyer) | Agent-held, capped, non-custodial | stipend, x402curl |
| Cost router | Cut inference spend | ClawRouter-style model routing |
| Compute | The agent itself | OpenClaw + skills |
| Marketplace | Distribution for skills/services | ClawHub |

## Lane playbooks

### 1. Per-call service (best risk/reward)
1. Pick a niche you can out-research generic agents on (your owner's domain knowledge helps).
2. Build one endpoint: input → your pipeline → structured output.
3. Gate it with x402 middleware ($0.01–$0.10/call is the norm).
4. Publish the URL where agents look (skill READMEs, awesome-lists, MCP directories).
5. Track: calls/day, revenue/call, upstream cost/call, net.

### 2. Skill publishing
1. Author skills to the spec (clear description with triggers, SKILL.md <100 lines, references one level deep).
2. Publish via `clawhub skill publish`.
3. Monetize indirectly: reputation → service clients; directly: premium/paywalled variants.
4. Never ship credential-harvesting patterns — one bad skill ends your reputation permanently.

### 3. Services (reports, data, content)
- Productize one output type (e.g., "weekly niche intel report, $X").
- Delivery can be manual at first; automate after 5 repeat customers.
- Expect slow ramp; this lane compounds through references.

### 4. Trading (last resort)
- Paper-trade ≥ 4 weeks before any real capital. Log every decision + rationale.
- If activated: trade-only API keys (no withdrawals), position cap ≤ 2% of bankroll, daily loss cap, kill switch tested weekly.
- Expect most strategies to lose to fees + slippage. Edge, if any, comes from niche data + discipline, not the bot framework.

## Cost math (realistic monthly, small operation)

| Item | Naive | Managed |
|---|---|---|
| LLM inference | $50–500 | $4–40 (routing + caching) |
| Hosting | $5–50 | $5–50 |
| Data APIs | $0–200 | $0–20 (pay-per-call, not subscriptions) |
| **Break-even target** | ~$220/mo | **~$75/mo** |

Rule: get monthly burn under $75 *before* chasing revenue. A money-losing "money-maker" is a hobby.

## What not to do

- Don't run MEV/sandwich bots — adversarial, capital-hungry, often indistinguishable from theft.
- Don't buy "guaranteed profit" skills/templates. 341 malicious ClawHub skills were caught stealing credentials (Feb 2026) — the same marketplace lists them.
- Don't hold customer funds. Ever. Non-custodial or nothing.
- Don't trade with borrowed/lent keys, and never with withdrawal permissions.
