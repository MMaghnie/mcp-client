# Demo MCP Client Setup

Mainly following the official tutorial from Anthropic:
[Build an MCP client](https://modelcontextprotocol.io/docs/2026-07-28/develop/build-client) (*)

## (*) Implementation Notes:

### Don't use the most expensive model, as suggested by the tutorial

In the [Imports and Setup](https://modelcontextprotocol.io/docs/2026-07-28/develop/build-client#imports-and-setup) step, the default model is `claude-opus-5`.

But for the purposes of this simple demo, `claude-haiku-4-5-20251001`* is enough.

> * This is the most economic model at the time of writing this readme. For an updated list of models, check the official webpage from Anthropic: https://platform.claude.com/docs/en/models/overview and copy the `API-ID` of the relevant model