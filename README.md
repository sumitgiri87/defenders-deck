# Defender's Deck

![Status](https://img.shields.io/badge/status-demo--ready-brightgreen)
![Format](https://img.shields.io/badge/format-offline%20single%20file-blue)
![Topic](https://img.shields.io/badge/topic-agentic%20AI%20threat%20modeling-red)

> A facilitator-driven, **offline** threat-modeling exercise for a live audience. The room
> threat-models one AI agent together — as **defenders** — and the deck reveals where each risk
> lands in the **OWASP Top 10 for Agentic Applications (2026)** and the control that stops it.

Built for a 25-minute interactive slot at **Threat Modeling Connect, Toronto** —
*Security Posture of LLM and Agentic AI* (Oct 21, 2026).

---

## Run it

Double-click **`defenders-deck.html`**. That's it — no install, no server, no internet.
Press **F** for fullscreen on the projector.

| Key | Action |
|-----|--------|
| `→` / `←` | next / previous slide |
| `Space` | reveal the next layer on a card (risk, then control) |
| `R` | restart · `◐ Theme` | dark / light |

## What's inside

| Path | What |
|------|------|
| `defenders-deck.html` | The exercise. Self-contained: inline SVG diagram, inline QR, no dependencies. |
| `scenario/target-system.md` | "Ledger Buddy", the fictional AP agent the room defends. |
| `docs/facilitator-script.md` | Minute-by-minute run sheet + facilitation tips + fallback plan. |
| `docs/research.md` | Frameworks, incidents, and format research behind the design. |
| `docs/options.md` | The session options that were considered. |

## The exercise

Seven components of a realistic agent, each mapped to one OWASP Agentic risk and one control:

1. **Mail connector** → ASI01 Agent Goal Hijack → *isolate untrusted content*
2. **Browser tool** → ASI01 exfiltration (lethal trifecta) → *egress allowlist*
3. **Shared service account** → ASI03 Identity & Privilege Abuse → *least privilege*
4. **Payments draft** → ASI02 Tool Misuse → *human approval*
5. **Auto-updating connector** → ASI04 Agentic Supply Chain → *tool vetting + pinning*
6. **Cross-user memory** → ASI06 Memory & Context Poisoning → *scope & validate*
7. **No tool-call logging** → detection gap → *log every tool call*

It closes on the **lethal trifecta** (private data + untrusted content + an outbound channel)
and an eight-item **defense checklist**.

## Design stance

It's a **blue-team** exercise. There's no live attack, no exploit code, and no
vulnerable-by-design target — the room supplies the threats; the deck supplies the OWASP
mapping and the controls. Everything is fictional.

## Credits & references

- [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026) — CC BY-SA 4.0, OWASP GenAI Security Project
- [CSA MAESTRO](https://cloudsecurityalliance.org/blog/2025/02/06/agentic-ai-threat-modeling-framework-maestro)
- Lethal trifecta — Simon Willison
- QR generated with [segno](https://github.com/heuer/segno)

Licensed under Apache 2.0.
