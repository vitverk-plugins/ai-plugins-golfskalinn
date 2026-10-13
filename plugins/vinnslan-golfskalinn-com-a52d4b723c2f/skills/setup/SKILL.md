---
name: setup
description: Set up or diagnose this Vinnslan plugin, sign in when needed, and verify accessible capabilities without changing customer data.
---

# Set up Vinnslan

This is the Vinnslan · Golfskálinn plugin. It targets only https://vinnslan.golfskalinn.com/mcp, with MCP server name `vinnslan-golfskalinn-com-a52d4b723c2f`.
A setup request authorizes connection checks and starting sign-in, not choosing permissions,
reading private document contents, changing customer data or granting additional access.

## Check the connection first

Use available host tool discovery (including deferred tools) to find this instance's tools.
Call get_instance when available and verify the returned origin before using other tools. Then
check accessible workspace, website-project and resource metadata as available and consented.
Start workspace discovery with vinnslan_list_workspaces({}). For paginated checks, omit limit
to use the default page size and follow nextCursor until absent.
Do not read document contents or run reports during setup. If connected, say so briefly and offer
useful next actions; reuse that connection instead of starting another login.

## If tools are missing

Check the installed plugin and its bundled MCP server through supported host/plugin diagnostics.
A plugin can load skills while failing to load its server. The standalone CLI's mcp get/list reads
separately configured servers; a missing entry there does not prove a plugin-owned server is absent
or unauthenticated. Do not ask the user to authenticate a server you have not found.

If the installed plugin resolves zero servers, refresh its marketplace and update that existing
plugin using supported host controls when available. Do not add a separate MCP server or reinstall
another copy. This package uses .codex-plugin/plugin.json and .mcp.json because the pilot desktop
build ignored bundled MCP configuration when a portable root plugin.json was present. Confirm
server discovery after the update. If a host refresh or new chat is needed, ask only for that next
action; do not give a sign-in checklist before the server is available.

## Help finish sign-in

For a discovered server that needs authentication, initiate the host's supported login action when
available. If the host exposes only a connection control, guide the user to that installed plugin's
Connect/Authenticate control, using the actual displayed name.

In Codex desktop, when the installed plugin and bundled endpoint are verified but this chat cannot
use its tools or operate connection controls, open [Finish connecting Codex](https://vinnslan.golfskalinn.com/external-access/mcp#mcp-codex-sign-in)
in the built-in browser. Use an available browser-opening tool such as open_in_codex with a browser
URL target; reuse this instance's tab when possible. The fragment reveals and focuses the help panel.
Give one concrete next action: click [Open Codex settings](codex://settings), choose **MCP servers**,
and find the existing server shown on that page. Select **Authenticate** if offered. Name the plugin
**Vinnslan · Golfskálinn** in the message and keep the help link visible. If the server is missing or disabled,
ask for that state and refresh/enable the existing plugin through supported controls. Missing tools
alone do not prove the user is signed out or denied access. Opening Vinnslan's help does not start OAuth.

The native Settings link is for the human to click; do not pass it to a tool that only supports web
URLs. If no built-in browser tool is available, provide the help link and the same next action.
In Claude, use its confirmed plugin's connection control or Customize → Connectors.

Use a CLI login only for an existing separately configured server whose name and endpoint you
have verified. In that case, start and track
`codex mcp login vinnslan-golfskalinn-com-a52d4b723c2f --oauth-client-registration dcr` if the CLI is already available.
Do not install a CLI or use this command as a probe for plugin-owned servers.

Ask the human to complete account sign-in and review permissions on https://vinnslan.golfskalinn.com. This does not prevent
you from initiating login, checking status or finishing the remaining setup. Request only the user
action currently needed; keep permission selection and the final Connect click with them. Explain
only permissions relevant to their intended work. Returned data leaves Vinnslan's sandbox.
Never ask for secrets in chat or manufacture a login URL. Do not create parallel login attempts or
replay a pending login. After approval, a blocked callback can use “finish signing in” on the approval
page; restart only an expired or definitively failed request.

## Verify and finish

Refresh discovery and repeat missing read-only checks. A successful authenticated tool result
verifies access; browser approval alone does not. Preserve successful checks when another fails.
Report the confirmed instance and useful available capabilities briefly. Mention a missing permission,
owner enablement or resource assignment only when it blocks the requested next action; do not present
a long list of unchecked categories. Existing roles, reviews, hook enablement and promotion controls
still apply. When blocked, state the concrete cause and next action instead of quoting this skill's
consent boundaries as a reason to stop helping.
