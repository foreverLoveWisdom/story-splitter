# Acceptance Criteria

## The One Thing

Good acceptance criteria are **testable, user-focused, and limited to 3-5 per story**.

## Why 3-5 Acceptance Criteria?

**Too few (1-2)**:
- Story too vague
- Missing edge cases
- QA can't test thoroughly

**Too many (9+)**:
- Story too large
- Multiple features bundled
- Needs breakdown

**Just right (3-5)**:
- Clear scope
- Independently testable
- Fits in one sprint

## Given-When-Then Format

```
Given [situation]
When [action]
Then [outcome]
```

**Example**:
- Given I enabled notifications
- When temporary error occurs
- Then I still receive notification eventually

## User Perspective vs Engineer Perspective

✅ **User Perspective** (correct):
- "When I click Save, Then settings update"
- "When temporary error occurs, Then I still get notification"

❌ **Engineer Perspective** (wrong):
- "When API returns 500, Then system retries"
- "When timeout occurs after 30 seconds, Then..."

Users don't see HTTP codes or timeouts - write ACs from their viewpoint.

## AI Collaboration Context

Story-splitter prompts generate Given-When-Then format automatically. Review output to ensure:
- All ACs are user-focused (not technical)
- Count is 3-5 per story
- Each AC is independently testable

## Learn More

**[BDD and Gherkin Syntax →](https://cucumber.io/docs/gherkin/reference/)**
