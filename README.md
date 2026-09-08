# Demo MCP Client Setup

Mainly following the official tutorial from Anthropic:
[Build an MCP client](https://modelcontextprotocol.io/docs/2026-07-28/develop/build-client)

## Implementation Heads-Up:

These notes are specifically about the [Imports and Setup](https://modelcontextprotocol.io/docs/2026-07-28/develop/build-client#imports-and-setup) step.

### Don't use the most expensive model, as suggested by the tutorial

The tutorial suggests using `claude-opus-5` as the `MODEL`.

But for the purposes of this simple demo, `claude-haiku-4-5-20251001`* uses fewer tokens and performs well enough.

> \* This is the most economic model at the time of writing this readme. For an updated list of models, check the official webpage from Anthropic: https://platform.claude.com/docs/en/models/overview and copy the `API-ID` of the relevant model

### If syncing to a remote repo, confirm `.env` is properly gitignored

The tutorial currently suggests using a command to add `.env` to `.gitignore` which doesn't actually let `.env` be ignored. 

Confirm the file is correctly ignored to protect your LLM API key.