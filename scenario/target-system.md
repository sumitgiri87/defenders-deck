# Reference system: "Ledger Buddy" (fictional)

A neutral, realistic agent used as the shared subject for the Defender's Deck.
This file describes the system as an architect would hand it to a threat-modeling
room. There are no exploits here — the room supplies the threats, the deck supplies
the OWASP mapping and the controls.

**Maple Ledger Co.** is a fictional Toronto fintech. Its accounts-payable team uses an
internal assistant, **Ledger Buddy**, to triage vendor email, look up invoices,
research vendors on the web, and prepare payment drafts for human approval.

## Components
| # | Component | What it does | Why a defender cares |
|---|-----------|--------------|----------------------|
| C1 | Employee chat UI | SSO-authenticated AP staff talk to the agent | The only *trusted* human input path |
| C2 | Ledger Buddy agent | Planner loop + LLM; runs under one shared service account | Holds the blast radius |
| C3 | Mail connector (MCP) | `read_inbox`, `send_email` | Pulls attacker-controllable text into context; can send data out |
| C4 | Drive connector (MCP) | `read_drive` over the finance share | Reads invoices, payroll, customer list |
| C5 | Browser tool | `fetch_url`, open internet | Pulls untrusted web content in; URLs can carry data out |
| C6 | Payments connector (MCP) | `create_payment_draft` → human approver in ERP | The high-value action |
| C7 | Agent memory | Vector store of past chats + vendor notes, shared across users | Persistent, cross-user context |
| C8 | Logs | App logs only; tool calls not logged separately | Limits what a responder can reconstruct |

## Design facts the room should notice
- Vendor email and web pages land in the **same context window** as the employee's instructions.
- The agent's **single service account** can read the whole finance share, not just what the
  requesting employee is cleared for.
- `send_email` and `fetch_url` are both **outbound channels** that can carry data off-box.
- The mail connector is a third-party component that **auto-updates**.
- Memory written in one person's session is **readable in everyone's**.
- Tool calls aren't logged on their own, so after an incident there's little to reconstruct.

## The eight deck cards map to these components
The facilitator walks the room through each component, the room names the risk and a
control, then the deck reveals the OWASP Agentic ID and the recommended defense.
