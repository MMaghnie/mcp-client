# Demo MCP Client Setup

Mainly following the official tutorial from Anthropic:
[Build an MCP client](https://modelcontextprotocol.io/docs/2026-07-28/develop/build-client)

## Implementation notes:

These notes are specifically about the [Imports and Setup](https://modelcontextprotocol.io/docs/2026-07-28/develop/build-client#imports-and-setup) step.

### Don't use the most expensive model, as suggested by the tutorial

The tutorial suggests using `claude-opus-5` as the `MODEL`.

But for the purposes of this simple demo, `claude-haiku-4-5-20251001`* uses fewer tokens and performs well enough.

> \* This is the most economic model at the time of writing this readme. For an updated list of models, check the official webpage from Anthropic: https://platform.claude.com/docs/en/models/overview and copy the `API-ID` of the relevant model

### If syncing to a remote repo, confirm `.env` is properly gitignored

The tutorial currently suggests using a command to add `.env` to `.gitignore` which doesn't actually let `.env` be ignored. 

Confirm the file is correctly ignored to protect your LLM API key.

## Good-to-knows:

* The call to `Anthropic()` (Line 15) must happen *after* loading env vars (Line 12), so the LLM API key gets properly populated in the LLM Client SDK.

* Where is the MCP server launched exactly? The server is launched by `stdio_client` (Line 132), using the description built by `server_params` (Line 18).

### Under the hood - usage of JSON-RPC methods 

* Line 132, `async with Client(...) as client:`, is where the initial `server/discover` method gets called, for the MCP client and server to get to know each other.

* Line 133, `await client.list_tools()`, sends the actual `tools/list` request from the MCP client to the MCP server, effectively asking "what tools do you have?".

* Line 71 executes `tools/call` 

## Heads-up about extending this demo:

The code in this demo is intentionally kept simple for training purposes and it's not production-ready. 

**Some** reasons:

* The `server_params` function detects server type simply by a naive file extension check. Anything can be renamed to use any file extension postfix, even malicious files.

* No error handling for server file path.

* Nothing checks what's exactly at the server path before running it.

