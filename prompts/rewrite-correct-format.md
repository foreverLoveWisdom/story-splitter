# Rewrite Story in Correct Format

**When to use**: Story is unclear or missing acceptance criteria

---

## Copy This → Paste into ChatGPT/Claude

```
Rewrite this user story in the correct format. Rules:

- Start with: "As a [who], I want to [what], So that [why]"
- Add 3-5 acceptance criteria (not more)
- Each acceptance criteria must follow this format:
  Given [situation]
  When [user does something]
  Then [system responds]
- Remove technical details (no file names, no code)
- Use simple language

Here is my story:

[PASTE YOUR STORY HERE]
```

---

## Example

**Before** (unclear):
"Add button to delete files. Users click it and file goes away."

**After** (correct format):

User Story:
As a user, I want to delete uploaded files, So that I can remove mistakes

Acceptance Criteria:

AC1: Delete button visible
Given I uploaded a file
When I view the file list
Then I see a "Delete" button next to each file

AC2: Confirm before deleting
Given I click the "Delete" button
When the confirmation dialog appears
Then I can choose "Yes" or "Cancel"

AC3: File removed
Given I confirm deletion
When I return to the file list
Then the deleted file is no longer visible
