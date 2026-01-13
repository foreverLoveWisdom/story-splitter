# User Story Format

## The One Thing

Good user stories explain **WHO** needs **WHAT** and **WHY** it matters.

## Standard Format

```
As a [who]
I want [what]
So that [why]
```

## Why Each Part Matters

**As a [who]**:
- Identifies the user persona
- Clarifies perspective (end user vs admin vs engineer)
- Prevents generic "the system" statements

**I want [what]**:
- Describes specific capability or feature
- Focuses on outcome, not implementation
- Keeps scope small and testable

**So that [why]**:
- Explains business value
- Helps team prioritize
- Enables negotiation about HOW

## Common Mistakes

❌ "As a system, I want to send emails..." → Systems aren't users
❌ "I want a button..." → Too implementation-focused
❌ "So that the database updates..." → Technical detail, not business value

## Examples

✅ "As a user, I want to receive notifications, So that I stay informed"
✅ "As an admin, I want to see usage metrics, So that I can plan capacity"

## AI Collaboration Context

All story-splitter prompts expect this format. AI uses:
- **[who]** to determine perspective (user vs engineer)
- **[what]** to scope the story
- **[why]** to validate if breakdown makes sense

## Learn More

**[Mike Cohn on User Stories →](https://www.mountaingoatsoftware.com/agile/user-stories)**
