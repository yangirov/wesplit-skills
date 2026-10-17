---
name: wesplit-batch-expenses
description: Record multiple explicitly requested purchases using one scoped, idempotent MCP batch.
---

# Batch expenses

- Parse each title, amount, date, payer and split. Apply message-wide instructions unless overridden.
- Read saved preferences once; verify event, participants and currency. Ask only for essential missing details.
- Call `wesplit_create_purchases_batch` with one stable `batchId`, exact ordered items and Unix millisecond dates. No enable switch or spending cap applies.
- Preserve the exact batchId and payload for retries. Inspect per-item results and disclose partial success. Do not claim atomicity.
- Respect host approvals and access permissions. Summarize confirmed purchases and totals.
