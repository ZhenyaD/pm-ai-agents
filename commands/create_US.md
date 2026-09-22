---
description: Create user stories in Jira from artifacts or my input, matching my example format
---
Use the ba-agent.

Parse $ARGUMENTS for the target workspace (default test) and the
source (UI flow, PRD, website URLs, or a free-text description).

Follow .claude/knowledge/ba/us-rules.md and study the screenshots in
.claude/knowledge/ba/us-examples/ — match their structure, fields, and
acceptance-criteria style exactly.

Steps:
1. Derive a list of stories with titles, descriptions, and acceptance criteria.
2. Show me the full list for review (do NOT create anything yet).
3. On approval, confirm the Jira project key, then create the issues in the
   target workspace and return the issue keys/links.