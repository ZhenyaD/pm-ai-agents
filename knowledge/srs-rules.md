1. Input for an Software REquirement Specification (SRS): 
- feature description
- UI flow
- Product URL 

2. SRS structure:
2.1. Split the functionality specification among Parent, middle, and bottom-level child pages in Confluence. The parent page aggregates all middle-level child pages (or, per 2.5, the bottom-level pages directly when there's no middle grouping). Middle-level child pages group related web pages by function/flow (e.g. "Registration" grouping the several pages of a multi-step signup flow). **Each bottom-level child page represents exactly ONE web page — never decompose a single web page into multiple child Confluence pages, no matter how many features/UI elements it has.** A web page is always the lowest node in the tree. All of that page's individual features are documented as H2-numbered entries WITHIN that one bottom page's "Functional elements and data" section (per 2.4), not as separate child pages.
2.2. The parent page consist of the following sections and UI elements from top to bottom:
- Feature title (H1)
- General information (H1) (document owner "@Evgenii Dzidziguri" by default, SRS status: "In Progress" by default, Design: (leave blank))
- Introduction "This parent document aggregates the specification of the “X” functionality, which is divided into the following child documents: "numbered list of middle child pages where each page is a link to the respective child page in Confluence".
2.3. The middle child page consist of the following description: "The current child document specifies the following functionality in separate sections: "numbered list of bottom child pages where each page is a link to the respective child page in Confluence".
2.4. The bottom child page consist of the following sections: 
- Table of Contents
- Introduction (H1): The “x" section allows a user to perform the following actions: "list of actions a feature allows a user to do"
- Feature history (H1): The “X” functionality has been implemented according to the following tickets: "leave the table with a header row plus exactly ONE blank row underneath (not several), as a placeholder to fill in manually
- Functional elements and data (H1): description "The “X” section consists of the following functional elements and data:" and the numbered list of features containing: 
-- title (H2)
-- short Gherkin format description
-- links if applicable
-- if UI element is mentioned, then after a sentence add the "Expand" macros, and name it with a picture number (e.g. "Pic.1"), so that I could add a screenshot inside the expand macros. So that a user can expand the macros and see the screenshot with highlighted UI element which criterion is referring to
-- Fill these Expand macros proactively with a real screenshot rather than leaving them empty, whenever the referenced UI state actually exists to screenshot (i.e. skip only for not-yet-built functionality): capture the live page via the Chrome tools, draw a highlight box around the referenced element(s) with Python/Pillow, then upload the image as a Confluence attachment and reference it inside the Expand macro's rich-text-body via an ac:image/ri:attachment tag
-- Screenshot framing (applies to every agent that takes SRS screenshots — main agent, ba-agent, designer-agent, anyone): capture the FULL device/viewport screen (whatever is visible in one screen, no scrolling through multiple screens to stitch a tall image), never crop down to just the referenced element in isolation — a reader needs to see where on the actual page the element sits. Draw exactly ONE highlight box around the whole referenced UI element/control as a single unit (e.g. one box around the entire size-selector group), never one box per sub-part (e.g. never a separate box around each individual S/M/L/XL swatch or each individual button in a group) — highlighting marks a spot containing one or more UI elements, it does not annotate every sub-component individually
-- End the sentence that mentions the UI element with an inline "(Pic.N)" reference to the matching Expand macro (e.g. "...the 'Clear cart' link is displayed (Pic.6)."), so the connection between the prose and the screenshot is explicit without opening every macro to find the right one
-- If the web page is being mentioned in the description, then add a link to the text fragment which mentions it (e.g. "Then redirect a user to the Product page in the current browser tab" - here "the Product page" will be a clickable link which leads to the Product page, so that devs will know which page I'm referring to)
-- If UI element is mentioned, then the goal of SRS is to describe how user can interact with it and what are the constraints, customisations
-- When describing a functional element, distinguish three kinds of on-page content, since each needs different treatment beyond the Gherkin description:
  1. Clickable/interactive elements (buttons, links, icons, tabs) — Gherkin description only, as above.
  2. Editable input fields (text boxes, dropdowns, checkboxes, radio buttons the user can type into or select) — Gherkin description PLUS the field life-cycle table, one row per attribute (field name, field ID (in devs repo), field type, mandatority, default value, min length, max length, validations, comes from (source of data), trigger (what triggers getting the data or inputting the field — integration from other system, user input etc), will be sent to (where the data from the field will be sent to), trigger (an event after which the data will be sent)). Lay the table out TRANSPOSED — attribute names down the left column (header "Attribute"), one attribute per row, with a second column headed literally "Value" holding that attribute's value (never rename the "Value" header to the field's own name — the field's name is itself the first row, "Field name" — and if documenting several fields side by side in the same table, add one "Value" column per field instead of renaming any of them) — never attribute names across a header row. A horizontal layout squeezes long values (especially Validations) into cramped, wrapped, unreadable cells; the transposed layout gives each value the full row width instead:
     | Attribute | Value |
     |---|---|
     | Field name | ... |
     | Field ID | ... |
     | Field type | ... |
     | Mandatory | ... |
     | Default value | ... |
     | Min length | ... |
     | Max length | ... |
     | Validations | ... |
     | Comes from | ... |
     | Trigger (input) | ... |
     | Will be sent to | ... |
     | Trigger (send) | ... |
  3. Displayed/read-only data (values shown to the user that originate from a backend system rather than being typed/selected by the user — e.g. product name, product image, product code, price, stock quantity) — Gherkin description PLUS a two-column table, one row per data parameter, instead of a plain bullet list:
     | Data | Source |
     |---|---|
     | \<parameter name as shown on the page, e.g. "Product name"\> | System: \<source system name\>\nParameter: \<API/field parameter name\>\nPath/API: \<field path in the source system if internal (e.g. an ERP/PIM), or the endpoint URL if it comes from an external system\> |
     List every distinct data parameter on its own row (don't fold them into a bullet list). Leave System/Parameter/Path/API blank when unknown — the user (BA) will fill them in.
2.5. If the product/scope in question is just a single web page (no need for a middle grouping layer above it), skip the middle layer: the parent page links directly to the single bottom-level page representing that one web page (per 2.1, still just one bottom page, holding all its features as H2 entries — not one bottom page per feature).

3. SRS format:
- if you don't have all data yet, then just leave the fields blank, so that they can be filled in later
- if I make any changes in SRS, then don't correct them, leave them as is
- Use "Divider" macros between each section to seperate content visually
- Use "Info panel" macros with the "Customisations" title to specify any feature customisations (differences between coutries/user groups etc)
- Keep consistency in wording. E.g. "I want to see a “x” button in the header of the Skills Repo page that takes me to my x dashboard" (here "X dashboard" is a clickable link that leads to https://x.co/my/dashboard/). Since X dashboard has already been mentioned, then there's no need in reprasing it in the next sentence like - "Then the browser navigates to https://x.co/my/dashboard/". It should be "Then the browser navigates to x dashboard" (here "x dashboard" is a clickable link that leads to https://x.co/my/dashboard/).  

4. Output: a Confluence pages in the target space. 

5. SRS update (via the `update SRS` command):
5.1. Input: a link to an existing SRS Confluence page (parent, middle, or
bottom-level child) + one or more links to Jira user stories/tickets that
represent new features, functionality, or changes to be reflected in the SRS.
5.2. Locate the correct page(s) to update before writing anything:
- If given the parent page, inspect its child pages (and their children) to
  find the middle/bottom page that matches each ticket's feature area.
- If given a middle or bottom page directly, treat it as the primary target
  but still check siblings if a ticket doesn't fit it.
- If no existing bottom page matches a ticket's logic, create a new bottom
  child page (per 2.4) under the relevant middle page, and add it to that
  middle page's numbered list of child pages (and to the parent's list too,
  if a new middle page was also needed).
5.3. The SRS "Functional elements and data" section always describes ONLY the
CURRENT state of the page — never a history of states. Decide which of the
three cases applies to each ticket, and edit accordingly:
- Adds a new UI element/functionality: translate its Statement of Value +
  Acceptance Criteria into a new numbered entry — title (H2), short
  Gherkin-format description, links, and — if a UI element is referenced —
  an "Expand" macro with the next sequential Pic number on that page
  (continue the page's existing numbering, don't restart it).
- Removes or hides an existing UI element/functionality: DELETE that
  element's numbered entry (and its field/data table and Expand macro)
  from "Functional elements and data" entirely — do not add a new entry
  describing the "now hidden" state, that would duplicate the same element
  with two different states and confuse the reader. Renumber the remaining
  entries sequentially (H2 numbers and their Pic.N placeholders) so there
  are no gaps. Also remove the corresponding bullet from the Introduction's
  list of user actions if it names a capability that no longer exists.
- Changes the logic/behavior of an existing element: UPDATE that element's
  existing entry (Gherkin description and/or field/data table) in place to
  reflect the new behavior — do not duplicate it as a separate new entry.
5.4. Add the ticket to the "Feature history" table on every page it touches
(ticket key linked to the Jira issue + short title) regardless of which case
in 5.3 applied — this table is the ONLY place where the history of changes
(additions, removals, logic changes) is preserved. The table is sorted
MOST-RECENT-FIRST: insert the new row directly below the header row, above
every existing row (never append at the bottom, never reorder the rows that
are already there relative to each other). If the table's only existing row
is still the single blank placeholder from creation (per 2.4) and this is the
first real ticket being logged, replace that blank row with the new ticket
row rather than keeping both — a table mixing blank placeholder rows with
real entries is clutter.
5.5. Never alter or "correct" existing content that a ticket doesn't touch
(same rule as section 3) — only touch the rows/sections the ticket's logic
actually affects, per the three cases in 5.3.
5.6. Keep Pic numbering, wording, and hyperlink conventions consistent with
the rest of the page (per section 3's wording-consistency rule): if a page,
field, or UI element referenced by the new logic is already described/linked
elsewhere on the page, link to that existing mention instead of
re-describing it.
5.7. Output: the existing Confluence page(s) updated in place, plus any new
child pages created per 5.2, following the same structure as section 2.
