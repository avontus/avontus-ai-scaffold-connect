# Avontus Viewer

Connects your AI assistant to the scaffold designs in your Avontus Viewer account, and adds a
skill for estimating scaffold labor.

## What's included

- **The Avontus Viewer connector** (`.mcp.json`), at `https://viewer-mcp.avontus.com/mcp`. You
  sign in with your Avontus Viewer account the first time it's used. The connector is
  read-only: nothing in the assistant can change or delete a design.
- **`avontus-viewer-estimating`**, a skill for estimating erection, modification and
  dismantling man-hours from a design's quantities, using the labor units and productivity
  factors from your own Schedule of Norms.
- **`avontus-viewer-designs`**, a skill for answering questions about designs: bills of
  materials, weights, parts by elevation, scaffold units and previews.
- **`avontus-product-help`**, a skill for how-to questions about any Avontus product, answered
  from the Avontus documentation at docs.avontus.com.

Setup: [Connect Avontus Viewer to Claude](../../docs/connect-to-claude.md).

## What this plugin connects to

- **One remote connector,** `https://viewer-mcp.avontus.com/mcp`, run by Avontus. Requests go only
  there, over HTTPS, after you sign in with your Avontus Viewer account on an Avontus page. The
  connector returns data from your own Avontus Viewer account and designs shared with you.
- **The skills are instructions only.** They run no code, install nothing and send no data.
- Nothing else is fetched, installed or run. Avontus's handling of the data is described in the
  [privacy policy](https://www.avontus.com/privacy-policy/).

## Requirements

An Avontus Viewer account with an active subscription. Scaffold units need designs exported from
Avontus Designer 6.10.1396 or later.

## Supported assistants

Claude. The connector itself also works in ChatGPT; this plugin package is Claude's format.

## Support

support@avontus.com

Copyright (c) 2008-2026 Avontus Software Corporation. All rights reserved. See [LICENSE](LICENSE).
