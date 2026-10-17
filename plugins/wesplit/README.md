# WeSplit skills

Seven public skills and an OAuth MCP connection for shared expenses.

## Install through Plugin Creator

[Download the plugin ZIP](https://github.com/yangirov/wesplit-skills/releases/latest/download/wesplit.zip), attach it to Plugin Creator in ChatGPT Work mode, and send:

> Добавь этот готовый плагин WeSplit в мой аккаунт ChatGPT. Сохрани его навыки и подключение к существующему MCP https://we-split.ru/mcp с OAuth.

The archive includes root `plugin.json`, `mcp.json` with an OAuth-protected Streamable HTTP connection, and seven skills. After import, check that both the skills and the MCP connection were saved. A successful plugin creation alone does not verify MCP import or authorize your account. Start the MCP connection in the intended host and approve only intended events and permissions in WeSplit. Test in a new chat with “Show my events”.

If the imported plugin has no connection action, even when it lists “MCP servers: 1”, use the [documented registered-MCP workflow](https://developers.openai.com/plugins/build/plugins#create-and-test-a-plugin-locally-with-an-mcp-server): in ChatGPT Plugins choose **+ → Add custom MCP server**, enter `https://we-split.ru/mcp` and OAuth, then choose **Create as a plugin**. Give Plugin Creator the resulting plugin link and this ZIP, and ask it to add the skills to that existing plugin while preserving its connection. Complete OAuth yourself, then verify a read-only tool in the intended host. Do not copy someone else's app ID into the public archive.

Public distribution source: https://github.com/yangirov/wesplit-skills. This ZIP is not a listing in the public ChatGPT plugin directory.

## Skills

- `wesplit-setup`: choose an accessible event, verified payer, participants and timezone.
- `wesplit-add-expense`: prepare and record one expense with user approval.
- `wesplit-batch-expenses`: record a list of purchases and inspect every result.
- `wesplit-receipts`: interpret a receipt photo and verify totals.
- `wesplit-reports`: spending, participant shares and balances for a period.
- `wesplit-expense-management`: find, correct or delete a purchase with approval.
- `wesplit-settlements`: record an already completed repayment with approval.

## Security and limitations

Every request enforces OAuth or personal-token rights and current event membership. Every mutation follows prepare, user review and commit. If a commit response is lost, check its durable status before retrying.

Receipt images are interpreted by the model; the MCP server does not ingest receipt files. Saved preferences are scoped to the authenticated account. Public packages contain no application source, credentials or account data.

A plugin card URL and a plain visit to `/mcp` or `/mcp/connect` are not OAuth authorization URLs. The client must initiate authorization with its own callback, state and PKCE. Report installation, completed OAuth and a successful read-only tool call as separate results; never claim a working connection solely from imported `mcp.json`.
