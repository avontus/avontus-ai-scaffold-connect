# Avontus AI Scaffold Connect

Plugins and skills that connect Avontus scaffold software to AI assistants.

| Plugin | Product | Status |
|---|---|---|
| [`avontus-viewer`](plugins/avontus-viewer) | Avontus Viewer | In preparation |

Each plugin lives in its own folder under `plugins/`, with its own manifest, connector and skills,
so each product can be listed and updated independently. What each connector can do is stated
per plugin: the Avontus Viewer connector is read-only, but connectors for other Avontus products
may not be.

## Getting started

- **Avontus Viewer:** [Connect Avontus Viewer to Claude](docs/connect-to-claude.md)

## Install in Claude Code

```
/plugin marketplace add avontus/avontus-ai-scaffold-connect
/plugin install avontus-viewer@avontus-ai-scaffold-connect
```

## Support

Avontus support: support@avontus.com. Privacy policy: https://www.avontus.com/privacy-policy/

Copyright (c) 2008-2026 Avontus Software Corporation. All rights reserved. See [LICENSE](LICENSE).
