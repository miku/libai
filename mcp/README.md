# Model Context Protocol

> The Model Context Protocol (MCP) is built on a flexible, extensible
> architecture that enables seamless communication between LLM applications and
> integrations.

One issue with LLM is halluciation and a common solution is similarity search
and RAG. MCP tries to expose data to an LLM client in a structured way.

> Servers provide context, tools, and prompts to clients

> MCP is not coupled to Zed or to Anthropic; since it's a protocol and not a
> library, anyone can use it without depending on any of our code. --
> https://zed.dev/blog/mcp

Types of messages:

* requests (expect response)
* notifications (one-way)
* results
* errors

MCP follows the idea of LSP.

## Library context

* we have catalog search, query to index
* we could have an MCP server frontend that exposes the resources (indices, url, digitized assets, website content, events, ...) to an LLM
* user can connect with an MCP client of choice, some desktop version, maybe mobile app, it's quite new, so not a lot of adoption

In any case, even if MCP is not successful, the category might be. A middleware
that can support LLM type apps with structured, exact data.

## MCP Resource

> [docs](https://modelcontextprotocol.io/docs/concepts/resources)

Resources represent any kind of data that an MCP server wants to make available
to clients. This can include:

* File contents
* Database records
    * L: results to search queries
* API responses
* Live system data
    * L: access status
* Screenshots and images
    * L: https://digital.ub.uni-leipzig.de/mirador/index.php
* Log files
* And more

### Resource discovery

> Clients can discover available resources through two [main
> methods](https://modelcontextprotocol.io/docs/concepts/resources#direct-resources):

* direct

```json
{
  uri: string;           // Unique identifier for the resource
  name: string;          // Human-readable name
  description?: string;  // Optional description
  mimeType?: string;     // Optional MIME type
}
```

* templates

```json
{
  uriTemplate: string;   // URI template following RFC 6570
  name: string;          // Human-readable name for this type
  description?: string;  // Optional description
  mimeType?: string;     // Optional MIME type for all matching resources
}
```

URI template RFC: [https://www.rfc-editor.org/rfc/rfc6570](https://www.rfc-editor.org/rfc/rfc6570).

Client asks for resources, with a [read request](https://modelcontextprotocol.io/docs/concepts/resources#reading-resources).


