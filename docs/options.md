# Session options

All options use the same fictional target (`scenario/target-system.md`) and fit 25 minutes.

## Lightweight (static, no model at runtime, near-zero demo risk)

### L1. "Threat Model It Live" (clickable page, the room drives)
One offline HTML page showing the Ledger Buddy diagram. The room calls out entry points;
you click a component and its attack path lights up, mapped to an OWASP ASI ID and a fix.
Ends with a lethal-trifecta overlay and the defense checklist.
- Build: ~2–3 h · Risk: very low · Wow factor: medium

### L2. "Which one hijacks the agent?" (spot the injection)
Six artifacts the agent will read: an email, a web page, a README, an MCP tool
description, a calendar invite, and a PDF. Tables vote on which ones are malicious (show of
hands), then you reveal what the agent would do. Too close to the 7:20 Slido quiz, so this
only works as a 5-minute warm-up.
- Build: ~1–2 h · Risk: very low · Wow factor: medium

## Agent-based (live model via `claude -p`, plus recorded fallback)

### A1. "Confused Deputy, Live" (attack, then harden) ⭐ recommended core
A small Python agent loop with 5 mock tools. Round 1: the audience picks one of the
planted payloads (or suggests a twist) and watches the agent leak payroll.xlsx to a fake
inbox. Rounds 2–5: turn on one defense at a time (least privilege, approval gate,
untrusted-content isolation, egress allowlist, audit log) and replay. The room predicts
whether each defense holds. At least one of them won't, which shows why injection can't
be fixed in the model.
- Build: ~4–5 h incl. recorded fallback · Risk: medium (mitigated by fallback) · Wow: high
- Covers every advertised bullet of the original talk almost 1:1

### A2. "Humans vs the AI threat modeler"
The room threat-models Ledger Buddy for 8 minutes (Slido word cloud or shout-outs).
Meanwhile a Claude Code **skill** (STRIDE + MAESTRO + OWASP ASI) produces its own threat
model. Diff them on screen: what humans caught that AI missed, and the reverse. Bridges
straight from Dr Li Yang's "Can we trust AI to automate security?" talk.
- Build: ~2–3 h · Risk: low-medium · Wow: high for this crowd

### A3. Red agent vs Blue agent tournament
An attacker agent generates injections, a target agent runs them, and a judge agent
scores them. The audience picks the defenses. Most impressive, but has the most moving
parts and non-deterministic output. Not for tomorrow.
- Build: 8 h+ · Risk: high

## Recommendation
**A1 as the spine with A2 as the closer, and L1's page as the slides and fallback.**
- 0–3 min   framing: "agents are deputies", lethal trifecta, ASI list on one slide
- 3–15 min  A1 live: attack, then 4 defense rounds with room predictions
- 15–23 min A2: room threat model vs AI threat model, discussion
- 23–25 min checklist slide + QR code to the repo
If time is short tonight: ship A1 + the checklist only. L1 alone is the safe floor.
