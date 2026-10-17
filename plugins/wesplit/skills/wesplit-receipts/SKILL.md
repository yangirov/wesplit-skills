---
name: wesplit-receipts
description: Interpret a receipt photo and record verified expenses through WeSplit MCP.
---

# Receipt capture

- Extract visible merchant, date, items, discounts, taxes, total and currency. Never invent illegible values.
- Reconcile the total and ask one focused question when material values are ambiguous.
- Default to one expense per receipt unless the user requests item-level purchases.
- Resolve a named event via `wesplit_list_events` and `wesplit_get_event`; otherwise use scoped `wesplit_get_preferences`. Explicit event selection never changes saved preferences.
- Verify the payer, participants, event currency and payment method ID. For item-level allocations use exact `allocations` and matching `members`. Do not infer payer from a receipt.
- Check `wesplit_list_purchases` for plausible duplicates before writing.
- For explicit recording requests use `wesplit_create_purchase` or `wesplit_create_purchases_batch` with explicit event IDs when selected and stable idempotency IDs. No spending cap or Quick Add switch. Respect host approvals and report confirmed writes only.
