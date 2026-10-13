---
name: website-development
description: Directly develop the customer website in Vinnslan boxes from an ordinary Codex chat without SSH or a local checkout.
---

# Vinnslan · Golfskálinn — website-development

Use only the MCP server named `vinnslan-golfskalinn-com-a52d4b723c2f` at https://vinnslan.golfskalinn.com/mcp for this customer.
Fetch private context live. Plugin files never confer permissions. Each capability requires separate
native consent at https://vinnslan.golfskalinn.com/external-access/mcp. Existing gadget consent grants none of these.
Returning data to Codex is explicit external access; Vinnslan cannot restrict its subsequent use.
Never put operational data, private documents, tokens or infrastructure credentials in this package.


The public website project ID is `golfskalinn`; still verify current membership with list_website_projects.
Use start_website_session with a fresh request UUID, then status until ready. This external session
never starts Vinnslan's editing agent. All files, commands, logs and submission use plugin tools.
No SSH session, local checkout, customer cloud login or infrastructure key is needed or appropriate.
Read files with their fileRevision and session revision. Preserve both when writing. Reconcile conflicts
by rereading. Keep one mutation in flight; retain every request ID and receipt.
Commands return a tracked job. Poll website_job until terminal, and use cancel_job when necessary.
A disconnected request, timeout, unknown job or missing reply is not permission to rerun a command.
Inspect website_operation and job first. Reuse an ID only with its identical original payload.
Unknown file writes/submissions freeze the writer for inspection; never work around this by replaying
under a new ID. An older runtime without commandJobs support must be updated by the operator.
Inspect preview status, logs, website_inspect screenshots and every changed file, including omitted/binary changes. Submit the exact
checkoutRevision returned by changes, with the current session revision. Native automated review
and PR checks still apply. Share the preview and PR for review. Submission grants no promotion
permission. Delivery tools require separate consent and the existing technical-admin group; inspect
promotion_plan for the exact SHA and never bypass review or switch environments to avoid a gate.
