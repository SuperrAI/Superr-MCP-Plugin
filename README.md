# Superr MCP plugin for Cursor and Grok Bot

Connects Cursor and Grok Bot to [SuperrPaper](https://superr.ai/mcp), a
handwriting-first notebook app for iPad.

This repository is the plugin manifest. The MCP server itself is hosted at
`https://mcp.superr.ai/mcp`; there is nothing to install or run locally.

## What it does

SuperrPaper has no keyboard by design, so everything on a page was written with
an Apple Pencil or spoken aloud. This plugin lets an agent work with those
notebooks:

- browse folders and notebooks, and read what is actually on a page, including
  the handwriting, typeset documents, notes, cards, templates and shapes
- write back: add a well-typeset document, place notes or shapes beside existing
  handwriting, import an article into a notebook
- reorganise notebooks, and add, move or remove pages

Anything written lands on the person's real page and syncs to their iPad.

## Access

The server reaches only that person's own notebooks and the ones already shared
with them. Authentication is OAuth 2.1 with PKCE against Superr's identity
service; the scopes are `notebooks.read` and `notebooks.write`, and access can
be revoked at any time from the SuperrPaper app.

No client credentials need to be configured here. The server publishes
[RFC 9728](https://datatracker.ietf.org/doc/html/rfc9728) protected-resource
metadata and supports both RFC 7591 dynamic client registration and Client ID
Metadata Documents, so the client registers itself and runs the flow.

## Installing

Add this plugin from the Cursor marketplace, then sign in when prompted. You
will need a SuperrPaper account, created by signing in on the
[iPad app](https://apps.apple.com/us/app/superrpaper/id6778513466).

## Links

- Documentation: https://superr.ai/mcp
- Support: hey@superr.ai
- Privacy policy: https://superr.ai/privacy-policy

## Licence

MIT, see [LICENSE](LICENSE).
