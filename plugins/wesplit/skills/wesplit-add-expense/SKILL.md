---
name: wesplit-add-expense
description: Record one explicitly requested WeSplit expense using the standard reviewed MCP workflow.
---

# Add a purchase

Use when the user asks to record a single expense.

1. Resolve the event with `wesplit_list_events` and `wesplit_get_event`. Identify the exact payer and split participants from the request or ask one focused question if essential information is missing. Never guess event, payer, amount, currency or participants.
2. Parse the title, positive amount and date. Use the event currency and a real Unix millisecond timestamp for the intended local date. Preserve any explicitly requested split and payment method.
3. Call `wesplit_prepare_purchase_change` with `kind: "createPurchase"` and the exact event, currency and purchase details. Show the returned summary and obtain the required user approval.
4. Call `wesplit_commit_change` only with the approved `changeId`. If the result is uncertain, call `wesplit_get_change_status`; never prepare a duplicate replacement.
5. Report success only after a confirmed commit, with event, amount and payer. Host approvals and credential permissions always apply.
