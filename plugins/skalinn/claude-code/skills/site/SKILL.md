---
name: site
description: Make a change to the Skálinn website in a hosted box and return a review packet, without submitting it.
argument-hint: "<change>"
context: fork
agent: skalinn:website-developer
disable-model-invocation: true
---

# Website change for Skálinn

Make this website change and check it in its preview: $ARGUMENTS

Return the review packet; do not submit.

If the skalinn:website-developer subagent is unavailable, follow this plugin's own workflow skill directly.
