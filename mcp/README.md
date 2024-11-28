# Model Context Protocol

> The Model Context Protocol (MCP) is built on a flexible, extensible
> architecture that enables seamless communication between LLM applications and
> integrations.

One issue with LLM is halluciation and a common solution is similarity search
and RAG. MCP tries to expose data to an LLM client in a structured way.

> Servers provide context, tools, and prompts to clients

Types of messages:

* requests (expect response)
* notifications (one-way)
* results
* errors

## Library context

* we have catalog search, query to index
* we could have an MCP server frontend that exposes the resources (indices, url, digitized assets, website content, events, ...) to an LLM
* user can connect with an MCP client of choice, some desktop version, maybe mobile app, it's quite new, so not a lot of adoption

In any case, even if MCP is not successful, the category might be. A middleware
that can support LLM type apps with structured, exact data.
