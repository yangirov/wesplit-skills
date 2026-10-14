---
name: wesplit-reports
description: Summarize and analyze actual WeSplit spending for dates, events and payers, including "yesterday" requests.
---

# Spending reports

- Resolve the intended event via saved defaults or an explicit name; if ambiguous, ask.
- Compute "today"/"yesterday" and calendar periods in the user's saved IANA timezone, not UTC or the system default.
- Use `wesplit_get_report` and paginate until complete for a requested detailed breakdown; do not infer yesterday's spending from the latest few purchases.
- Separate total spending, paid-by-user amounts, individual shares and net balance. They are different metrics.
- Do not combine currencies without an explicit rate source/date. Do not invent categories absent from stored data; if grouping is heuristic, label it.
- Present a short answer with actual totals and a concise breakdown. State when data is unavailable or incomplete.
