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
A plugin can load skills while failing to load its server. CLI versions differ in plugin support;
a negative standalone mcp get/list result does not prove a plugin-owned server is absent or
unauthenticated. Prefer the bundled plugin-aware helper below. Do not ask the user to authenticate
a server you have not found.

If the installed plugin resolves zero servers, refresh its marketplace and update that existing
plugin using supported host controls when available. Do not add a separate MCP server or reinstall
another copy. This package uses .codex-plugin/plugin.json and .mcp.json because the pilot desktop
build ignored bundled MCP configuration when a portable root plugin.json was present. Confirm
server discovery after the update. If a host refresh or new chat is needed, ask only for that next
action; do not give a sign-in checklist before the server is available.

## Help finish sign-in

For a discovered server that needs authentication, initiate the host's supported login action when
available. Otherwise use the bundled connection helper when Node is available; it finds the existing
CLI or a bundled macOS app-server executable without requiring a terminal step from the user.
From this installed plugin's root, run `node scripts/connect-codex.mjs --check`; the script is at
`../../scripts/connect-codex.mjs` relative to this skill's directory. An available host runtime tool
can supply Node's path. Do not install a runtime or CLI to complete setup.

The helper checks the installed plugin identity and origin through Codex's public app-server API.
`connected` confirms helper-side authentication; still verify this chat's tools. Only
`authentication_required` calls for running the same helper with `--login`, once. Keep that command
and its subprocess session alive. On `awaiting_sign_in`, open its exact returned authorizationUrl
in the built-in browser and ask the human to sign in, review access and click Connect. Track the
matching completion; then refresh discovery and verify authenticated tools. Never reconstruct a
login URL or automatically replay a pending/interrupted helper. `pending` requires inspecting the
existing command before any restart; an expired receipt still needs manual recovery. `unavailable` or `blocked` calls for the manual page below.
A successful browser approval or helper completion alone does not prove this chat has loaded tools.

If the host exposes only a connection control, guide the user to that installed plugin's
Connect/Authenticate control, using the actual displayed name.

In Codex desktop, when the installed plugin and bundled endpoint are verified but this chat cannot
use its tools or operate connection controls, open [Finish connecting Codex](https://vinnslan.golfskalinn.com/external-access/mcp/connect?method=manual)
in the built-in browser when no supported login action or helper is available. Use an available
browser-opening tool such as open_in_codex with a browser URL target; reuse this instance's tab when possible. This dedicated page shows only the connection steps.
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
