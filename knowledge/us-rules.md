1. Input for a user story: 
- provided Figma file / screenshot of a new designed feature
- a URL / screenshot of a page where a new feature needs to be added
- feature description

2. User story sections: 

2.1. Statement of Value
- Written in a format: As a user...I want...So that...

2.2. Acceptance Criteria
- Each criterion starts with a criterion number and a short name explaining the use case (e.g. "AC 1 - Display the stock for a dealer"). Do not highlight them in bold.
- Acceptance criteria is written in Gherkin format
- If there's a reference in the text on some UI element, then after criterion add an "Expand" macro, and name it with a picture number (e.g. "Pic.1"), and add a screenshot inside the expand macros. So that a user can expand the macros and see the screenshot with highlighted UI element which criterion is referring to
- Fill these Expand macros proactively with a real screenshot rather than leaving them empty, whenever the referenced UI state actually exists to screenshot: capture the live page via the Chrome tools, draw a highlight box around the referenced element(s) with Python/Pillow, then attach it to the Jira issue — since there's no direct Jira attachment-upload API tool, do this via browser automation: open the description editor, place the cursor in the target Expand macro's body, use the image-insert toolbar button, and upload to the media-picker's file input with the file_upload tool (never click the Upload button directly, that opens an unreachable native OS dialog)
- End the criterion's sentence that mentions the UI element with an inline "(Pic.N)" reference to the matching Expand macro (e.g. "...the 'Download cart' button and its tooltip are not displayed (Pic.1)."), so the connection between the criterion and the screenshot is explicit without opening every macro to find the right one
- If the web page is being mentioned in the criterion, then add a link to the text fragment which mentions it (e.g. "Then redirect a user to the Product page in the current browser tab" - here "the Product page" will be a clickable link which leads to the Product page, so that devs will know which page I'm referring to)
- Divide each criterion with a blank line

2.3. Additional Details
- This section might contain any additional information which will help developers, like: links to the design mockups / user flows, API description

3. User story format:
- Use "Divider" macros between each section to separate content visually
- Use "Info panel" macros for the entire "Additional Details" section to visually separate additional details from the main requirements listed in Statement of Value and Acceptance criterion sections
- Don't put a comma or period at the end of a sentence
- Keep consistency in wording. E.g. "I want to see a “Jinni” button in the header of the Skills Repo page that takes me to my Djinni dashboard" (here "x dashboard" is a clickable link that leads to https://x.co/my/dashboard/). Since Djinni dashboard has already been mentioned, then there's no need in reprasing it in the next criterion like - "Then the browser navigates to https://x.co/my/dashboard/". It should be "Then the browser navigates to Djinni dashboard" (here "x dashboard" is a clickable link that leads to https://x.co/my/dashboard/).  

4. Output: a Jira ticket in the target space with:
- issue type: Story
- title format: <short action>
