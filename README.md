# Requirements Breakdown Prompts

Turn 50-point stories into 3-8 point stories in 60 seconds.

## The Problem

Your user story takes 2-3 sprints instead of 1. Why?

It bundles 5+ features into 1 story.

## The Solution

2 copy-paste prompts for ChatGPT/Claude.

## How to Use (3 Steps)

1. Open [Prompt 1](prompts/1-break-down-large-story.md)
2. Copy → Paste into ChatGPT with your story
3. Done. You have 3-8 point stories with 3-5 acceptance criteria

## Real Example

**Before**: 1 story, 50 points, took 6 weeks

**After**: 10 stories, 48 points total, delivered in 6 weeks (on time)

[See the breakdown →](examples/after-good-stories.md)

## 2 Prompts

1. **[Break Down Large Story](prompts/1-break-down-large-story.md)** → Story takes > 1 week
2. **[Rewrite Correct Format](prompts/2-rewrite-correct-format.md)** → Story is unclear

## Story Size Guide

- **3 points** = 2 days
- **5 points** = 3 days
- **8 points** = 5 days (MAX)

If > 8 points → Use Prompt 1

## Good vs Bad Acceptance Criteria

**Good**:
```
Given I upload a file
When I click "Delete"
Then the file disappears
```

**Bad**:
```
Call FileService.delete(uuid) method
Update database table files
Redirect to /files/index page
```

Why bad: Shows HOW (code), not WHAT (user action)

---

**License**: MIT
