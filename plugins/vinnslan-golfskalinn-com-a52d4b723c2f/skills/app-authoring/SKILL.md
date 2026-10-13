---
name: app-authoring
description: Create and edit native Vinnslan app drafts, outputs and persistent workflow code using Codex directly.
---

# Vinnslan · Golfskálinn — app-authoring

Use only the MCP server named `vinnslan-golfskalinn-com-a52d4b723c2f` at https://vinnslan.golfskalinn.com/mcp for this customer.
Fetch private context live. Plugin files never confer permissions. Each capability requires separate
native consent at https://vinnslan.golfskalinn.com/external-access/mcp. Existing gadget consent grants none of these.
Returning data to Codex is explicit external access; Vinnslan cannot restrict its subsequent use.
Never put operational data, private documents, tokens or infrastructure credentials in this package.


Use app_start_draft in an existing authorized build workspace, then app_create for a provisional app
or edit an existing gadget. A null model prevents an embedded Vinnslan editing agent from starting.
Record returned IDs immediately. Never automatically replay interrupted draft/app creation; inspect
the native workspace first. Read draft_status, pinned commits and exact source before editing.
For write_file preserve clientId and monotonically increasing seq, with only one submission in flight.
Retry transport loss only with the same seq and identical payload. Permanent unpinned gadgets need
the current accepted baseCommit. Native OT handles concurrent changes and rejects invalid history.
Bind only existing authorized resources, with separate category consent. Run native validation and
hermetic tests at the exact generation/revision. Inspect the app in its native preview sandbox;
a UI bundle URL needs the Vinnslan host and is not a standalone public website. Accept the reviewed
position through app_accept; conflicts and native validation remain authoritative.
Output access requires outputs consent. List export formats, then export accepted output contents.
Inline exports are bounded; use the native output link for larger files.
Persistent schedules and portal tools use register_workflow with the accepted callback gadget's
commitId and restore params. Read automation_resource_api for recurrence and options; include an
explicit timezone for calendar schedules. Retain its requestId and inspect its receipt after a lost
reply. Unknown registration never permits a new request ID to repeat it.
Registration remains disabled until the user enables its hook in native Connections. Portal audience
assignment remains native. Do not substitute a Codex automation: execution belongs in Vinnslan and
must continue with Codex closed.
