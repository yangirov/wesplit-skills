---
name: wesplit-quick-add
description: Record one explicit shared expense from a short message or voice command using WeSplit saved defaults, without repetitive follow-up questions.
---

# Record an expense quickly

Use when the user clearly says to add or record one expense (for example "Аптека 3000 йен").

1. Call `wesplit_get_preferences` to resolve active event, payer, split members and timezone. The user's explicit values override saved defaults. If defaults are absent, or multiple events/participants match, ask only the one indispensable question. Never guess.
2. Parse the exact positive amount, title, currency and local expense date. Verify the event currency and use its correct minor-unit precision, with at most two decimal places supported by the existing purchase store. Ask for clarification rather than rounding unsupported precision. Date must be a real Unix millisecond timestamp in the configured timezone. Do not assume UTC midnight is the user's local day.
3. If the user explicitly asked to record and saved Quick Add is enabled, use `wesplit_create_purchase` with a stable unique `requestId`; preserve the ID and exact payload across retries after ambiguous responses. Never choose a new requestId to evade a failure.
4. If Quick Add is off, use `wesplit_prepare_purchase_change`; show the exact summary, ask for necessary approval, and commit only after it. Do not pretend the original request was a separate confirmation for the legacy prepare/commit tool.
5. Respect host/platform approvals, configured limits and access permissions. Do not mislabel financial mutations as read-only or bypass authorization.
6. Report success only after the server confirms it, e.g. "Добавлено: Аптека, ¥3000 → Япония." If a response is uncertain, state uncertainty and check durable status where supported. Never duplicate uncertain expenses.
