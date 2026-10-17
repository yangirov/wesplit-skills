# WeSplit skills

Seven public skills and an OAuth MCP connection for shared expenses.

## Install in Codex

Run with a current Codex CLI:

```sh
codex plugin marketplace add yangirov/wesplit-skills
codex plugin add wesplit@wesplit
```

Restart Codex. Connect the WeSplit MCP server at https://we-split.ru/mcp using OAuth and grant only intended events and permissions. Installation does not sign you in or authorize expense creation.

[Download the plugin ZIP](https://github.com/yangirov/wesplit-skills/releases/latest/download/wesplit.zip) for compatible plugin clients. Public source: https://github.com/yangirov/wesplit-skills. This is a GitHub distribution, not a listing in the ChatGPT plugin directory.

## Skills

- `wesplit-setup`: choose an accessible event, verified payer, participants and timezone.
- `wesplit-add-expense`: record a short expense such as “Pharmacy 3000 yen”.
- `wesplit-batch-expenses`: record a list of purchases and inspect every result.
- `wesplit-receipts`: interpret a receipt photo and verify totals.
- `wesplit-reports`: spending, participant shares and balances for a period.
- `wesplit-expense-management`: find, correct or delete a purchase with approval.
- `wesplit-settlements`: record an already completed repayment with approval.

## Fast expense entry

Save event, payer, split and timezone preferences with `wesplit_set_preferences` when requested. Direct expense tools record explicit purchases without an enable switch or monetary cap. OAuth rights and host approvals remain enforced. Deletion and repayments retain reviewed commands.

## Security and limitations

Every request enforces OAuth or personal-token rights and current event membership. Direct purchases require scoped saved preferences, current write access and stable idempotency keys. Batch requests may partially succeed: inspect each item. Replay only with the same batchId and identical payload.

Receipt images are interpreted by the model; the MCP server does not ingest receipt files. Saved preferences are scoped to the authenticated account. Public packages contain no application source, credentials or account data.
