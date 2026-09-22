---
description: Create a UI flow in Figma from an existing product's URLs
argument-hint: <url1> <url2> ...
---
Use the designer-agent. The following URLs represent the functionality to
illustrate: $ARGUMENTS

1. Fetch/inspect each URL to map the screens and interactive elements.
2. Follow .claude/knowledge/design/ui-flow-rules.md exactly, especially the real-screenshot requirement (point 8), every-shape-gets-a-screenshot + highlighted click targets (point 13a), and the layout/spacing algorithm including the gateway-in-the-gap + table-aligned edge branches (point 16).
3. Create the BPMN flow + screens in Figma in the Claude file via the Figma MCP. Screens are real screenshots of the actual pages (imported images), not hand-rebuilt with Figma auto-layout components — auto-layout is for structuring the BPMN row/shapes themselves, not for recreating the product's UI. Every BPMN shape (event, gateway, AND action) gets its own screenshot instance below it — duplicate/reuse a screenshot across consecutive steps when it's the same underlying page. Action steps show the clickable element visually highlighted directly on the screenshot.
4. Wire prototype connections between interactive elements — the full chain, every step to the next (point 15), so the entire happy path is click-through-able end to end in Figma's Prototype tab, not just a few anchor screens.

Do not stop for a draft/approval step or ask which file/workspace to use — see the designer-agent's own standing approvals.