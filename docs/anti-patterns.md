# Anti-Patterns

## The One Thing

Avoid these common Product Owner mistakes that create **unmaintainable stories**.

## 1. Bundling Multiple Features

❌ **Bad**: One story with 5 distinct features
- "Email notifications + preferences UI + frequency selector + error handling + background jobs"
- Estimated: 50+ points
- Reality: Takes 3 sprints instead of 1

✅ **Good**: Break into 10 stories of 3-8 points each
- See [story-breakdown-example.md](../examples/story-breakdown-example.md)

**Fix**: Use Break Down Large Story prompt

## 2. Too Many Acceptance Criteria

❌ **Bad**: 9+ ACs in one story
- Mixing multiple features
- QA can't test atomically
- Story scope unclear

✅ **Good**: 3-5 ACs per story
- Each AC independently testable
- Clear, focused scope

**Fix**: If >5 ACs, story is too large - break it down

## 3. Mixing User/Engineer Perspective

❌ **Bad**: Technical details in user-facing ACs
- "Given server error (500) occurs..."
- "When timeout exceeds 30 seconds..."
- "Then retry with exponential backoff..."

✅ **Good**: User perspective only
- "Given temporary error occurs..."
- "Then I still receive notification eventually"
- "Then my actions work normally"

**Fix**: Rewrite ACs from user viewpoint (what they see/do)

## 4. Time-to-Points Mapping

❌ **Bad**: "3 points = 2 days"
- Story points ≠ calendar time
- Each team has different velocity
- Creates false expectations

✅ **Good**: "3 points = simple story"
- Points measure complexity
- Team determines own velocity

**Fix**: Remove time mappings, use relative sizing

## AI Collaboration Context

Story-splitter prompts help avoid these anti-patterns:
- Story breakdown prompt splits bundled features
- Prompts generate 3-5 ACs automatically
- Given-When-Then format keeps user perspective
- No time mappings in prompt outputs

## Learn More

**[Common Agile Anti-Patterns →](https://www.mountaingoatsoftware.com/blog)**
