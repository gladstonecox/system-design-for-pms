# Workday Supplier Invoices

A practice system design for one feature: an AP clerk adds line items to a supplier invoice, and suppliers can send invoices directly into Workday. The same system is drawn three times, from a first draft to a version ready for a technical PM interview.

| File | Level of detail |
|---|---|
| [1-original-draft.md](1-original-draft.md) | The first draft: requirements, features, and a client / server / database diagram |
| [2-simplified.md](2-simplified.md) | The draft with the review applied, kept at the same level of detail |
| [3-interview-version.md](3-interview-version.md) | Full version for a Stripe-style interview: two request flows, state machine, and trade-offs |

## What changed from the draft

- **Two entry points.** The draft's features mention suppliers sending invoices through a queue and an API gateway, but the diagram showed only the clerk. Both paths are now drawn.
- **Numbered steps.** Every arrow has a step number, so the order of a request is clear.
- **Responses.** The clerk gets computed fields or field errors back. The supplier gets an immediate "received" (202) and the result later.
- **Duplicate protection.** Every write carries an idempotency key, so a retried request never creates a second invoice.
- **Invoice lifecycle.** The interview version adds the invoice state machine and the audit trail.
- **Stated assumptions and trade-offs.** Scale numbers to confirm with the interviewer, and one line of reasoning for each major decision.

## Editing the diagrams

Each diagram is a `mermaid` code block inside a Markdown file.

- **On GitHub:** the diagrams render on the file page. Click the pencil icon to edit from any device.
- **Visually:** copy a code block into [mermaid.live](https://mermaid.live) to edit with a live preview, then paste it back.
- **In VS Code:** the built-in Markdown preview renders Mermaid with the *Markdown Preview Mermaid Support* extension.
