# Superr MCP

Connect any MCP client to [SuperrPaper](https://superr.ai/mcp), a
handwriting-first notebook app for iPad.

The server is hosted at `https://mcp.superr.ai/mcp`. There is nothing to install
or run: this repository holds the connection details and the per-client manifests
that some directories require.

## What it does

SuperrPaper has no keyboard by design, so everything on a page was written with
an Apple Pencil or spoken aloud. Connected to this server, an assistant can:

- browse folders and notebooks, and read what is actually on a page, including
  the handwriting, typeset documents, notes, cards, templates and shapes
- write back: add a well-typeset document, place notes or shapes beside existing
  handwriting, import an article into a notebook
- reorganise notebooks, and add, move or remove pages

Anything written lands on the person's real page and syncs to their iPad.

## Connecting

| | |
|---|---|
| Server URL | `https://mcp.superr.ai/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth 2.1 with PKCE |
| Scopes | `notebooks.read`, `notebooks.write` |

No client credentials need configuring. The server publishes
[RFC 9728](https://datatracker.ietf.org/doc/html/rfc9728) protected-resource
metadata at `/.well-known/oauth-protected-resource/mcp` and supports both
[RFC 7591](https://datatracker.ietf.org/doc/html/rfc7591) dynamic client
registration and Client ID Metadata Documents, so a client registers itself and
runs the flow.

Most clients need only the URL. A few want it spelled out:

**Claude Code**

```
claude mcp add --transport http superr https://mcp.superr.ai/mcp
```

then `/mcp` to sign in.

**Anything reading a config file** (the same config is in [`mcp.json`](mcp.json))

```json
{
  "mcpServers": {
    "superr": {
      "url": "https://mcp.superr.ai/mcp"
    }
  }
}
```

**Cursor and Grok Bot** read `.cursor-plugin/plugin.json`, which points at
`mcp.json` in this repository.

## Access

The server reaches only the signed-in person's own notebooks and the ones
already shared with them. Access can be revoked at any time from the SuperrPaper
app.

You will need a SuperrPaper account, created by signing in on the
[iPad app](https://apps.apple.com/us/app/superrpaper/id6778513466).

## Links

- Documentation: https://superr.ai/mcp
- Support: hey@superr.ai
- Privacy policy: https://superr.ai/privacy-policy

## Licence

MIT, see [LICENSE](LICENSE).
