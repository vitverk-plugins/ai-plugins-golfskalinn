# Vinnslan · vinnslan.golfskalinn.com

This package connects only to https://vinnslan.golfskalinn.com/mcp. It contains workflow skills and public packaging
metadata, never credentials, private company context, operational data or permissions.
Use the current setup page at https://vinnslan.golfskalinn.com/external-access/mcp.

## Preferred: your organization's plugin

If your organization already offers this instance's plugin, add it from your client's plugin
directory and connect its Vinnslan service with your own account. Use the existing connection.
An administrator can distribute the customer plugin through the client's supported workspace or
organization marketplace. Staff do not need repository access when using that distribution.

## Codex desktop

Open **Plugins → Add marketplace** and enter the GitHub repository URL provided by the instance's
setup page. Install **Vinnslan · Golfskálinn**, then run the plugin's setup action or start a new chat and
say **Use the Vinnslan setup skill to check my connection**. The setup skill checks existing access
before asking you to sign in.

If connection setup needs help, open [Finish connecting Codex](https://vinnslan.golfskalinn.com/external-access/mcp#mcp-codex-sign-in).
That section shows this instance's existing server and an [Open Codex settings](codex://settings) link.
Choose **MCP servers**, find **vinnslan-golfskalinn-com-a52d4b723c2f**, and click **Authenticate** if offered.
In the browser, sign in to https://vinnslan.golfskalinn.com with the account you normally use there. Check the client and
instance, choose the permissions you want, and click **Connect**. Wait for Codex to confirm success.
If the browser return is blocked after approval, click **finish signing in** on that approval page.
Then ask **Check my Vinnslan connection**. Only successful authenticated tool calls prove connection.

This package uses Codex's compatibility manifest and bundled HTTP MCP configuration. The pilot
desktop build resolves the server from this format; it currently ignores the server when the
portable root manifest is present. Do not mix those entrypoints until the intended clients pass
connection tests. Update the existing plugin if it loads skills but no MCP server.

A plugin-owned server may not appear in `codex mcp get`, which reads separately configured
servers. Use the plugin's connection controls. For a separately configured server confirmed at
this exact origin, the existing DCR fallback is:

`codex mcp login vinnslan-golfskalinn-com-a52d4b723c2f --oauth-client-registration dcr`

Do not add another MCP server. Instance, marketplace and server names stay stable across updates.
Refresh the marketplace and update the existing plugin when a new version is published.

### ZIP and CLI fallback

If repository-based installation is unavailable, extract this ZIP into a permanent folder.
With the Codex CLI installed, open Terminal or PowerShell there and run:

`codex plugin marketplace add .`

`codex plugin add vinnslan-golfskalinn-com-a52d4b723c2f@vinnslan-golfskalinn-com-a52d4b723c2f`

Keep the extracted folder while using this local marketplace, then run setup as above.

## Claude web and desktop

Download **Claude plugin (.zip)** from https://vinnslan.golfskalinn.com/external-access/mcp. That download is a single
plugin with its manifest and remote MCP connection at the ZIP root. Upload it through
**Customize → Plugins**, review it and add the plugin. Open **Customize → Connectors**, find Vinnslan for **vinnslan.golfskalinn.com**,
and click **Connect**. In the browser, sign in to Vinnslan, review permissions and click **Connect**.
Return to Claude and ask **Set up my Vinnslan connection** to verify access.
This marketplace ZIP is for Codex/Claude Code; do not upload this outer package as a Claude plugin.
On supported organization plans, an owner can upload the single-plugin ZIP to a marketplace and
distribute it to staff. Client plan and organization policy determine availability.

For tools without bundled workflow skills, use **Customize → Connectors → Add → Custom → Web**.
Enter https://vinnslan.golfskalinn.com/mcp, review detected OAuth settings and choose sign-in. Use Claude's published
identity, or **Register automatically** if that method fails. No API key or client secret is needed.

## Claude Code

Prefer your organization's plugin or a supported Claude account plugin. For a local marketplace,
keep this extracted folder and run:

`claude plugin marketplace add . --scope user`

`claude plugin install vinnslan-golfskalinn-com-a52d4b723c2f@vinnslan-golfskalinn-com-a52d4b723c2f --scope user`

Restart Claude Code, enter `/mcp`, select this instance's plugin server and choose **Authenticate**.
Complete browser consent, then check `/mcp` again. Installing a local Claude Code plugin does not
configure Claude web or desktop chat. Use one connection route per client and instance.

## Installer fallback

Native macOS/Windows installers remain available from the setup page when published. They may
contain older bundled guidance; use that page's current sign-in instructions. Native installer
signing and publication are separate from generating this source package.

This source package also contains optional setup scripts. On macOS/Linux, run
`sh "Install Codex.command"` or `sh "Install Claude Code.command"`. On Windows, open
**Install Codex.cmd**; for Claude Code, use the marketplace commands above. These scripts copy the
package to an owned user data folder, register its catalog and install it through the client's CLI.
macOS supports Codex on PATH or inside the installed ChatGPT/Codex app. Windows/Linux need the CLI.
No administrator access is needed for source installation. Scripts never change execution policies.
After source installation you may delete the extracted download because the installer keeps a copy.

For Codex, open **Sign in to Codex.command** (macOS/Linux) or **Sign in to Codex.cmd** (Windows).
Current launchers use DCR and keep the login window open until success. The macOS/Linux managed
folder is ~/.local/share/vinnslan/plugins/vinnslan-golfskalinn-com-a52d4b723c2f; Windows uses LocalAppData/Vinnslan/Plugins/vinnslan-golfskalinn-com-a52d4b723c2f.
VINNSLAN_PLUGIN_HOME can override that parent. Rerunning updates only the installer-owned package;
an unmanaged destination is preserved. Registration or installation errors stop without granting access.

## Permissions and missing tools

Consent separately to workspace discovery, company context, business reads, development, outputs,
automation, commerce and delivery. Existing gadget access grants none of these automatically.
Consent never changes staff roles or bypasses approvals, review or technical-admin promotion controls.
Platform tools require the corresponding consent and accessible resources. Gadget tools additionally
require owner-enabled MCP support. Refresh tools or start a new chat after permission changes.
Visit https://vinnslan.golfskalinn.com/external-access/mcp to inspect connected clients, adjust optional permissions or revoke.

Each instance has a distinct plugin, server and catalog name. State the intended instance before a
write. Returned data leaves Vinnslan's sandbox; Vinnslan cannot control how the client subsequently
uses it with its other tools.

## Remote development and persistent execution

Website development uses authenticated plugin tools from an ordinary chat. Vinnslan provisions the
box and keeps infrastructure credentials server-side. No SSH chat or local checkout is required.
Retain mutation receipts, poll tracked command jobs, inspect previews and changes, then submit the
reviewed checkout through the existing PR pipeline. An operator must first install a box runtime
with persistent command jobs; older images refuse commands.
Native app drafts use existing validation, previews and acceptance. Persistent workflows run in
Vinnslan with the client closed; native hook enablement and audience controls remain required.
Medusa reads require the caller's existing assignment and role; commerce changes are not yet supported.
