---
name: wesplit-receipts
description: Extract merchant, date, amount, currency and items from a receipt photo and prepare a verified expense.
---

# Receipt capture

Use when the user sends a receipt photo with a request to record expenses.

- Extract visible merchant, local date, item list, discounts, taxes, total and currency using image understanding. Never invent illegible values.
- Reconcile the total against items, discounts and taxes. Ask one focused question if discrepancies affect the amount.
- Default to one expense for the whole receipt with merchant title and optional item notes. Split into multiple expenses only when requested.
- Resolve the exact event with `wesplit_list_events` and `wesplit_get_event`. Verify payer and split participants explicitly; the receipt alone does not establish who paid.
- Before writing, check plausible duplicates via `wesplit_list_purchases` (merchant, date, amount).
- Prepare using `wesplit_prepare_purchase_change`, show the exact summary, obtain required approval and commit via `wesplit_commit_change`. For an uncertain outcome check `wesplit_get_change_status`.
