---
name: wesplit-batch-expenses
description: Record several explicitly requested WeSplit purchases safely using individual reviewed commands.
---

# Batch expenses

When the user lists several expenses:

- Resolve the exact event using `wesplit_list_events` and `wesplit_get_event`. Verify its currency, participants and permissions.
- Parse each title, amount, date, payer and split. Apply message-wide instructions to all items unless overridden. Never invent missing essential details.
- Prepare each purchase through `wesplit_prepare_purchase_change`. Show the summaries for user review and obtain required approval before committing.
- Commit approved `changeId` values one at a time with `wesplit_commit_change`. There is no atomic batch write: report each confirmed outcome and any failures.
- For an uncertain commit use `wesplit_get_change_status`; never prepare an automatic replacement or duplicate a purchase.
- Finish with a compact count and sum in the event currency.
