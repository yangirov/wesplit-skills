---
name: wesplit-receipts
description: Extract store, date, amount, currency and items from a user-provided receipt photo and record a verified WeSplit expense.
---

# Receipt capture

Use when the user sends a receipt photo with a request to record expenses.

- Extract visible merchant, local date, item list, discounts, taxes, total and currency using image understanding. Never invent illegible values.
- Reconcile total against item amounts, discounts and taxes. If discrepancies affect the recorded total, ask one focused clarification.
- Default to ONE expense for the entire receipt with merchant title, optionally append item notes. Split into multiple expenses only if requested; use batch skill when applicable.
- Use saved event/payer/split defaults via `wesplit_get_preferences`; explicit user overrides win. The image alone does not establish who paid.
- Before any write check for possible duplicate receipt via `wesplit_list_purchases` (merchant, date, total). If duplicate is plausible, ask rather than recreate.
- Respect Quick Add limitations and host approval; otherwise follow prepare/review/commit. Never claim image OCR or write succeeded unless actually verified.
