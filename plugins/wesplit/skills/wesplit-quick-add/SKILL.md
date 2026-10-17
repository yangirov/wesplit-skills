---
name: wesplit-quick-add
description: Record one explicitly requested expense quickly using saved preferences and a direct MCP tool.
---

# Record an expense

1. Call `wesplit_get_preferences` to resolve the active event, payer, split members and timezone. Explicit user choices override defaults. If missing, verify via `wesplit_list_events` and `wesplit_get_event`; ask only one essential question at a time. Never guess.
2. Parse exact title, amount, currency and local date. Verify event currency and precision. Convert the intended local time to a Unix millisecond timestamp.
3. For explicit expense requests, call `wesplit_create_purchase` directly with a stable unique `requestId`. No Quick Add enable switch, spending cap or extra prepare/commit is required. Host approval and MCP permissions still apply.
4. After an uncertain response, retry only with the same ID and identical payload. Never create duplicate expenses.
5. Report success only after server confirmation. Never claim a purchase was saved merely because it was prepared.
