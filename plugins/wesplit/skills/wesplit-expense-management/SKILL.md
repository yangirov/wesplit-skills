---
name: wesplit-expense-management
description: Find, correct or delete an existing WeSplit purchase without changing unrelated fields or accidentally selecting a duplicate.
---

# Edit expenses safely

- Identify the target event from saved preferences or explicit user choice; fetch matching purchases with `wesplit_list_purchases` and paginate as necessary.
- "Last purchase" means most recent by actual stored chronology within the intended event; if ties or multiple candidates, clarify.
- For updates, retrieve original purchase data and preserve ALL unchanged properties, including split allocations and payment method.
- Prepare via `wesplit_prepare_purchase_change`, show exact financial consequences and obtain required approval. Commit only the prepared changeId.
- Treat deletion as destructive: identify exact record and ask for explicit confirmation.
- On uncertain result use `wesplit_get_change_status`, never create a new replacement command automatically.
