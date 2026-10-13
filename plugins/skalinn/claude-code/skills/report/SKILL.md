---
name: report
description: Answer a question about Skálinn's company data with a sourced, read-only report.
argument-hint: "<question>"
context: fork
agent: skalinn:analyst
disable-model-invocation: true
---

# Report for Skálinn

Answer this from Skálinn's data, read-only: $ARGUMENTS

If the skalinn:analyst subagent is unavailable, follow this plugin's own workflow skill directly.
