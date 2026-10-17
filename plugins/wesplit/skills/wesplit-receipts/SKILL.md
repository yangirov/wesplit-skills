---
name: wesplit-receipts
description: Interpret a receipt photo and record verified expenses through WeSplit MCP.
---

# Receipt capture

- Extract visible merchant, date, items, discounts, taxes, total and currency. Never invent illegible values.
- Reconcile the total and ask one focused question when material values are ambiguous.
- Default to one expense per receipt unless the user requests item-level purchases.
- Use `wesplit_get_preferences` and explicit user overrides to resolve event, payer and split. Verify event currency and permissions.
- Check `wesplit_list_purchases` for plausible duplicates before writing.
- For an explicit recording request use `wesplit_create_purchase` or `wesplit_create_purchases_batch` with stable idempotency IDs. No spending cap or Quick Add switch applies. Respect host approvals and report only confirmed writes.
