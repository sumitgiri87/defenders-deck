# Research notes

## What the room expects in this slot
The advertised session promised:
1. How tools, MCP-connected apps and browser agents expand the attack surface
2. The **confused deputy**: an agent tricked into using *its own* permissions for an attacker
3. Why prompt injection can't be fixed at the model level
4. Defenses: least privilege, human approval for high-risk actions, isolating untrusted
   content, tool vetting, activity logging
5. "Real-world scenarios and collaborative discussion" + a practical checklist

A replacement should hit the same beats so nobody feels short-changed. Audience = threat
modelers and AppSec people, so they'll want a system to model, not a lecture.

## Anchor frameworks (name-drop, don't teach)
- **OWASP Top 10 for Agentic Applications 2026** (Dec 2025), ASI01–ASI10:
  Goal Hijack · Tool Misuse · Identity & Privilege Abuse · Agentic Supply Chain ·
  Unexpected Code Execution · Memory & Context Poisoning · Insecure Inter-Agent Comms ·
  Cascading Failures · Human-Agent Trust Exploitation · Rogue Agents
  (verify names against genai.owasp.org before putting them on a slide)
- **CSA MAESTRO**: 7-layer agentic threat modeling (foundation model, data ops, agent
  framework, deployment infra, security/compliance, agent ecosystem, eval/observability)
- **Lethal trifecta** (Simon Willison): private data + untrusted content + an exfil channel
  means injection becomes data theft. A good mental model you can explain in one slide.
- STRIDE still works as the "familiar entry point" for this crowd

## Real incidents to cite
- EchoLeak (CVE-2025-32711): zero-click exfiltration via M365 Copilot
- Replit agent deleted a production DB during a code freeze
- Poisoned MCP tool descriptions / "rug pull" tool updates (tool-poisoning research, 2025)

## Format notes
- Interactive formats people liked at similar events: hands-on vulnerable chatbot labs,
  red/blue card games (e.g. Capture the Risk), live attack-then-harden demos
- Hands-on labs need laptops + Wi-Fi + setup time, so they're too risky for a meetup slot.
  Audience participation through a shared screen with you driving is the safe version.
