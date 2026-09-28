# Connect Avontus Viewer to Claude

Avontus Viewer connects Claude to the scaffold designs in your Avontus Viewer
account, so you can get answers from the design itself before the crew starts
loading: labor estimates from your own Schedule of Norms, bills of materials,
weights, parts by elevation, scaffold units, and a rendered preview of any
design, without opening the Viewer app.

There is nothing to download or install. You connect Avontus Viewer in Claude
and sign in with your existing Avontus Viewer account.

> This guide is also published on docs.avontus.com, as Connecting to Claude.

---

## Before you start

- An **Avontus Viewer account**: the same email and password you use to sign
  in to Avontus Viewer. You do not need a new account.
- An **active subscription**. Every design this connector reads is either
  yours or shared with you, and both require a live subscription. See
  [Subscriptions](#subscriptions) below.
- A **Claude account** on claude.ai, Claude Desktop or the Claude mobile apps.

---

## Connect from the Claude directory (recommended)

> **Coming soon.** Avontus Viewer is being added to the Claude connector
> directory. Until it appears there, use
> [Add as a custom connector](#add-as-a-custom-connector) below. It connects to
> the same service and works the same way.

### Pro, Max or Free

1. In Claude, open **Customize → Connectors** and select the **Discover** tab.
2. Search for **Avontus Viewer** and open it.
3. Click **Connect**. A sign-in page opens at `viewer-mcp.avontus.com`.
4. Sign in with your Avontus Viewer email and password, then approve access.

### Team or Enterprise

An organization Owner enables Avontus Viewer once. Each member then connects
their own Avontus Viewer account.

**Owner, once:**

1. Open **Settings → Organization settings → Connectors**.
2. Browse the directory, find **Avontus Viewer** and add it for your
   organization.

**Each member, once:**

1. Open **Customize → Connectors** and find Avontus Viewer in the list.
2. Click **Connect**, sign in with your own Avontus Viewer email and password,
   and approve access.

An Owner enabling the connector does not sign anyone in. Everyone signs in
individually, and each person sees only the designs their own Avontus Viewer
account can already see.

---

## Add as a custom connector

Use this method until the directory listing is available, or if your
organization does not use directory connectors.

You will enter two values. Both are the same for every customer, and neither
is a secret:

| Field | Value |
|---|---|
| Remote MCP server URL | `https://viewer-mcp.avontus.com/mcp` |
| OAuth Client ID | `viewer-connector` |

Leave **OAuth Client Secret** empty. There isn't one: Avontus Viewer signs you
in using PKCE, the method designed for apps that can't safely hold a secret.

### Pro, Max or Free

1. In Claude, open **Customize → Connectors**.
2. Click **Add**, then choose **Add custom connector**.
3. **Name**: type `Avontus Viewer`. This is only a label, so any name you will
   recognize works.
4. **Remote MCP server URL**: paste `https://viewer-mcp.avontus.com/mcp`
5. Expand **Advanced settings**.
6. **OAuth Client ID**: enter `viewer-connector`

   This step is required. If you skip it, the connector is added but sign-in
   fails.
7. **OAuth Client Secret**: leave empty.
8. Click **Add**.
9. On the Connectors list, click **Connect** next to Avontus Viewer. A sign-in
   page opens at `viewer-mcp.avontus.com`.
10. Sign in with your Avontus Viewer email and password, then approve access.

### Team or Enterprise

**Owner, once:**

1. Open **Settings → Organization settings → Connectors**.
2. Click **Add connector**, then choose **Custom**.
3. Enter the name `Avontus Viewer` and the URL
   `https://viewer-mcp.avontus.com/mcp`.
4. Under advanced settings, enter the OAuth Client ID `viewer-connector` and
   leave the secret empty.
5. Save.

**Each member, once:**

1. Open **Customize → Connectors** and find Avontus Viewer in the list.
2. Click **Connect**, sign in with your own Avontus Viewer email and password,
   and approve access.

### If you are already signed in

If you signed in to Avontus recently, the sign-in page shows **You're signed
in as** with your account. Choose **Continue** to use that account, or **Use a
different account** to sign in as someone else.

---

## Add the Avontus Viewer skills (optional)

The [Avontus Viewer plugin](../plugins/avontus-viewer)
adds skills that help Claude estimate labor with your own Schedule of Norms and
present design data consistently. The connector works without them.

- **Claude Code:**

  ```
  /plugin marketplace add avontus/avontus-ai-scaffold-connect
  /plugin install avontus-viewer@avontus-ai-scaffold-connect
  ```

- **claude.ai and Claude Desktop:** the plugin will be available from the
  Claude directory. Organization Owners can also add it for their whole
  organization.

---

## Use it in a conversation

When the connector shows as connected, click the **+** button in a
conversation, choose **Connectors**, and switch on Avontus Viewer.

Then ask Claude things like:

- *"Estimate erection man-hours for my stair tower design at 6 minutes per
  piece, with a 1.25 congestion factor."*
- *"List my Avontus Viewer designs and tell me which one is the heaviest."*
- *"Show me the preview for my stair tower design."*
- *"Give me the bill of materials for my pipe rack design, grouped by part
  type, with the total weight."*
- *"What are the scaffold units for my tank design?"*
- *"Sort the parts in my pipe rack design by elevation, bottom to top, then
  split them into 5 metric ton truckloads."*
- *"Which designs have been shared with me, and who owns them?"*

---

## Estimating labor

Avontus Viewer supplies the quantities: pieces, weight, volume, surface area,
leg length and decks. You supply the labor units and productivity factors,
from your own Schedule of Norms or your crews' recorded actuals. Claude applies
them and shows every step, for example:

> 157 pieces × 6 min = 942 min = 15.7 man-hours, then 15.7 × 1.25 = 19.6
> man-hours with a 1.25 congestion factor.

Claude asks how your factors combine rather than assuming, treats erection,
modification and dismantling separately, and never supplies a labor unit of
its own. There is no universal scaffold labor standard, and a rate that is not
your own can put a real bid at risk.

See [Estimating man-hours with a Schedule of Norms](https://docs.avontus.com/docs/estimating-man-hours-with-a-schedule-of-norms)
for the terminology and worked examples.

---

## What Claude can see

Claude can read, and only read:

- Your own designs, and designs shared with you
- Bills of materials with quantities and weights
- Parts grouped by elevation
- Scaffold units (surface area, volume, total leg length and similar)
- Design preview images
- Avontus product documentation at docs.avontus.com. Questions about
  inventory, rental, pricing or billing are answered from the Avontus Quantify
  documentation, and a request to design a new structure gets an explanation
  of how to build it in Avontus Designer.

Claude **cannot** create, change, share or delete anything in your Avontus
Viewer account. Every tool in this connector is read-only.

Claude only sees your designs after you sign in and approve access, and only
the designs your Avontus Viewer account already has access to. Your password
is entered on Avontus's own sign-in page and is never shared with Claude.
See the [Avontus privacy policy](https://www.avontus.com/privacy-policy/).

### US or metric

Every design is authored in one measurement system: **US** (feet, square feet,
cubic feet, pounds) or **metric** (meters, square meters, cubic meters,
kilograms). Claude reports each design in its own system unless you ask for
the other, and uses one system for the whole answer, never pounds alongside
meters. Tell Claude once, "use US" or "use metric", and it holds to that for
the rest of the conversation.

If any part has no weight recorded, the total weight is marked as a minimum
rather than quietly under-reported.

### Scaffold units

Scaffold units are the quantities Avontus Designer calculates for estimating
and billing, such as surface area, volume and total vertical leg length. They
are separate from the physical parts in the bill of materials, and are only
available on designs exported from Avontus Designer 6.10.1396 or later. For an
older design, Claude tells you its scaffold units are unavailable rather than
estimating them. Its bill of materials and elevations stay exact either way.

### Subscriptions

Uploading designs to Avontus Viewer requires an active **Avontus Designer**
subscription. Claude reads designs through this connector; it does not create
or upload them.

Whether a design can be read depends on whose design it is:

- **Your own designs**: your subscription must be active. If it has lapsed,
  Claude tells you the account needs unlocking rather than showing stale
  figures.
- **Designs shared with you**: the **owner's** subscription must be active,
  not yours. If theirs has lapsed, Claude names the owner and suggests
  contacting them.

---

## Disconnect

Open **Customize → Connectors**, find Avontus Viewer, and choose
**Disconnect**. Claude immediately loses access to your designs. Connect again
at any time by signing in.

---

## Troubleshooting

**Sign-in fails right after clicking Connect (custom connector).** The most
common cause is a missing or mistyped OAuth Client ID. Open the connector's
settings and confirm **Advanced settings → OAuth Client ID** reads exactly
`viewer-connector`, with the Client Secret empty.

**The wrong designs appear.** Confirm you signed in with the Avontus Viewer
account that owns the designs. Disconnect and connect again, and if the
sign-in page says "You're signed in as" someone else, choose **Use a different
account**.

**Claude says it can't find a design.** Ask it to list your designs first.
Design names in Claude match the names in Avontus Viewer exactly.

**Scaffold units are unavailable for an older design.** Designs exported by
older versions of Avontus Designer don't carry scaffold units. Bills of
materials still work. Re-exporting the design from a current version of
Avontus Designer adds them.

**Claude says a subscription has expired.** For your own designs, your Avontus
subscription needs renewing. For a design someone shared with you, the owner's
subscription has lapsed, and Claude names the owner so you know who to ask.

**The connector doesn't appear in a conversation.** Switch it on per
conversation with the **+** button → **Connectors**.

**The connector icon looks wrong or generic.** This is cosmetic and does not
affect the connection. Claude caches connector icons and refreshes them on its
own schedule.

---

## Support

Questions or problems: contact Avontus support at support@avontus.com.

Copyright (c) 2008-2026 Avontus Software Corporation. All rights reserved.
