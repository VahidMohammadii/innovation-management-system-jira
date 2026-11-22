# Jira Configuration Exports

**Status: Export collection planned — no machine-readable Jira configuration files are published here yet.**

I have documented the automation controls in the [rule catalog](../03-automation-rules/automation-rule-catalog.md) and the intended Stage-Gate flow in the [conceptual diagram](../01-system-design/conceptual-stage-gate-flow.md). Neither document should be mistaken for an export of enabled Jira rules or workflows.

## Planned contents

| Artifact | Intended format | Current status |
| --- | --- | --- |
| AUTO-01–AUTO-08 automation rules | Jira-generated JSON export, where supported | Not exported or committed |
| Stage and gate workflow definitions | Jira-provided export or documented workflow configuration | Not exported or committed |
| Jira custom fields and statuses | Reviewed configuration inventory | Not exported or committed |

Before committing an export, I will confirm that it corresponds to the current Jira setup and remove any credentials, tokens, private URLs, email addresses, account identifiers and other sensitive metadata. I will also document any manual redaction so that the published file is not misrepresented as an untouched original.

**This folder is an export-readiness index, not a substitute for actual Jira configuration files.**
