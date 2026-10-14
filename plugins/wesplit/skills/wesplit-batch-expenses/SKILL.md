---
name: wesplit-batch-expenses
description: Record several explicitly requested WeSplit purchases in one voice or text message, with safe retry and per-item results.
---

# Batch expenses

When the user lists 2-10 expenses together:

- Parse each item into title, amount, date and optional payer/split. Apply message-wide clauses (e.g. "all paid by me") to all items unless overridden.
- Fetch preferences once; use exact active event, IANA timezone, currency and split rules. Never invent omitted settings.
- Confirm ambiguous amounts or currencies only when essential.
- With Quick Add enabled and every amount within limit, call `wesplit_create_purchases_batch` with ONE stable `batchId`, an immutable ordered list, and dates in milliseconds. Preserve the same batchId and input for any retry.
- The batch API reports partial outcomes; report exactly which items were saved and which failed. Never claim that the entire batch was atomic.
- When Quick Add is disabled, use the reviewed prepare/commit workflow for each expense. Never bypass explicit tool approval or access controls.
- End with a compact count and sum in the event currency.
