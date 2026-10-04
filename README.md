# Milepost

Connect Claude to your Milepost Roadbooks, drafts, garage, profile, and friends'
shared drives. Review a trip's story and route, prepare a synced draft, update
your car's nickname, or catch up on drives your friends have shared with you.
The plugin includes four skills and connects to Milepost's 17-tool remote MCP
server at `https://milepost.club/mcp`.

## Install in Claude Code

Add the marketplace and install Milepost:

```sh
claude plugin marketplace add heysaik/milepost-claude-plugin
claude plugin install milepost@milepost-plugins
```

In a new Claude Code session, use `/mcp` to connect Milepost with OAuth. Enter
your Milepost handle in the browser, tap the approval notification in Milepost
on a registered phone, and review the requested permissions. The browser returns
to Claude after approval. No API key, Milepost password, or iCloud Keychain
credential is required. An updated Milepost installation with notifications
enabled is needed for approval.

If you already connected Milepost through Claude's connector settings, use that
connection. Both point to the same server; don't configure a second endpoint.

You can also clone this repository and load the plugin for one session:

```sh
claude --plugin-dir ./milepost-claude-plugin
```

## Try it

- "Show my latest Milepost drive and its note."
- "Find my newest synced draft and suggest a title."
- "Rename my Mazda MX-5 to Weekend in my Milepost garage."
- "Catch me up on my friends' recent Milepost Roadbooks."

The skills cover profile edits, garage management, drive and draft management,
and friends' shared Roadbooks. Publishing, widening visibility, reactions, and
comments require your explicit request. Edits use current revisions so an
outdated request cannot silently overwrite a newer save.

## Data and permissions

The plugin sends your requested tool arguments only to its declared Milepost
connector and returns the records allowed by your account's permissions. Those
records can contain your profile, vehicle details, drive dates, notes, and route
coordinates. Routes are requested only when needed and contain at most 500
points. Claude processes the conversation and tool results under its own terms.

Your Milepost data stays on Milepost's server under its normal sync, privacy,
retention, and deletion rules. This package has no local server, scripts, hooks,
extra data destinations, purchases, or independent data store. Claude manages
the scoped OAuth connection; this repository and its skills contain no tokens
or reviewer credentials. Adding a vehicle may request generic artwork through
Milepost's existing service, within its generation limits.

Milepost's server uses OpenAI to moderate outward-facing text and referenced
photos when you change information visible to others. Shared Roadbooks may also
send bounded text and photos for emoji selection, and generic vehicle artwork
uses the vehicle description. These are existing Milepost service operations
covered by its privacy policy; the plugin does not contact OpenAI directly.

Only synced data is available. The plugin cannot remotely record a drive, delete
drives or vehicles, delete an account, book or purchase anything, send direct
messages, or read another person's private drives. Claude Code uses text
responses; this version does not include custom graphical UI.

Use `/mcp` or Claude's connector settings to disconnect. Reconnect when a grant
expires or you need to approve additional scopes. Keep tool confirmation
prompts enabled. If a comment request has an uncertain result, read the current
comments before retrying to avoid posting it twice.

## Updates and support

```sh
claude plugin update milepost@milepost-plugins
```

[Milepost](https://milepost.club) · [Support](https://milepost.club/support) ·
[Privacy](https://milepost.club/privacy) · [Terms](https://milepost.club/tos)

The MIT license applies to these plugin files. It does not license the Milepost
app, server, artwork, trademarks, or user data. Use of the Milepost service is
subject to its Terms of Service.
