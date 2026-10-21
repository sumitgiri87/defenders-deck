# Facilitator script — Defender's Deck

**Slot:** replaces "The Agent Attack Surface", 6:50–7:20 PM, before the Slido quiz.
**You need:** a laptop + projector. Open `defenders-deck.html` in any browser (double-click it —
no internet, no server needed). Press **F** for fullscreen. That's the whole setup.

**Controls:** `→` next · `←` back · `Space` reveal the next layer on a card · `R` restart · `◐ Theme` toggles dark/light.

---

## Timing (25 min + 5 buffer)

| Time | Slide | What you do |
|------|-------|-------------|
| 0:00–2:00 | Title | Frame it: "The talk was about the agent attack surface. Instead of me lecturing, *we're* going to threat-model one agent together, as defenders." Explain: you call the risk, the deck reveals the OWASP landing + the fix. |
| 2:00–4:00 | The system | Walk the diagram once. Point out the 4 colors: trusted input (blue), untrusted content entering (red), outbound channels (amber), high-value action (green). Don't explain risks yet — just the architecture. |
| 4:00–18:00 | 7 cards (~2 min each) | **This is the session.** For each card: read the question, *ask the room out loud* ("what's the risk here? what would you do?"), take 2–3 answers, THEN press Space to reveal the risk, discuss, press Space again for the control. |
| 18:00–20:00 | Lethal trifecta | Tie it together: most of what they just found is one pattern. This is your "why prompt injection can't be fixed in the model" moment. |
| 20:00–22:00 | Checklist | The takeaway slide. "Eight controls — screenshot this." |
| 22:00–24:00 | OWASP Top 10 | Show the full list; note which ones tonight covered (highlighted) and which we didn't (ASI05 RCE, ASI07 inter-agent, ASI08 cascading, ASI10 rogue agents) — "material for the next meetup." |
| 24:00–25:00 | QR / thank you | Point to the repo QR. Hand off to the Slido quiz. |

---

## Running the cards (the important part)

Each card maps one **component** of Ledger Buddy to one **OWASP Agentic risk** and one **control**.

| # | Component | Lands at | Control |
|---|-----------|----------|---------|
| 1 | Mail connector (untrusted email in context) | ASI01 Agent Goal Hijack | Isolate untrusted content |
| 2 | Browser tool (untrusted web + private data + egress) | ASI01 → exfiltration | Egress allowlist; break the trifecta |
| 3 | Shared service account | ASI03 Identity & Privilege Abuse | Least privilege / per-user scoping |
| 4 | Payments draft (high-value action) | ASI02 Tool Misuse | Human approval (watch for ASI09 rubber-stamping) |
| 5 | Mail connector auto-updates | ASI04 Agentic Supply Chain | Tool vetting + version pinning |
| 6 | Shared cross-user memory | ASI06 Memory & Context Poisoning | Scope & validate memory |
| 7 | No tool-call logging | Cross-cutting (detection) | Log every tool call |

**Facilitation tips**
- The room *will* get most of these. That's the point — let them feel it. Your job is to name
  the OWASP label and sharpen the control, not to stump them.
- Cards 1 and 2 are the "confused deputy" heart of the original talk. Spend your energy there.
- If the room is quiet, call on people: "You're the AP manager — would you let it send email?"
- If you're running long, cards 5–7 can each be 60 seconds. Never cut the trifecta slide.
- If someone asks about live demos / jailbreaks: "Great thread — that's the red-team view.
  Tonight we're doing the blue-team view, which is the harder half." (And it keeps the room
  focused on things they can act on Monday.)

## Three provocations to keep in your back pocket (if discussion stalls or runs short)
1. "Human-in-the-loop is security theater once you're approving 500 drafts a day." Agree/disagree?
2. "Prompt injection will never be solved — stop trying and just sandbox." True?
3. "An AI threat modeler would have caught more of these than this room did." Would it?

## If the file won't open / projector dies
The whole thing is one HTML file and a Markdown scenario. Worst case, open
`scenario/target-system.md` and the checklist in `docs/` and run it as a whiteboard discussion
off the component table. The content stands without the app.
