# Requirements Breakdown Prompts

Turn 50-point stories into 3-8 point stories in 60 seconds.

## The Problem

Your user story takes 2-3 sprints instead of 1. Why?

It bundles 5+ features into 1 story.

## The Solution

2 copy-paste prompts for ChatGPT/Claude.

## Two Workflows

### Basic Flow (No Codebase Access)

Quick breakdown without technical context:

1. Open [Prompt 1](prompts/1-break-down-large-story.md)
2. Copy → Paste into ChatGPT/Claude with your story
3. Done. You have 3-8 point stories with acceptance criteria

**Use when**: Business-only features, UI changes, or no codebase access.

### Ideal Flow (With Codebase Scanning)

**For Product Owners with codebase access:**

Collaborate with [Claude Code](https://claude.ai/code) in terminal to scan your codebase first:

1. **Open terminal in your codebase** with Claude Code
2. **Let AI scan for relevant technical details**:
   - "Scan the codebase - how does file upload currently work?"
   - "Find all database tables related to authentication"
   - "Show me which services handle document processing"
3. **AI reads actual code** and explains architecture
4. **Copy technical context + business requirements**
5. **Use Prompt 1** with complete picture
6. **Get realistic breakdown** based on real architecture

**Why codebase scanning matters:**
- ✅ Discovers hidden dependencies (3rd party APIs, shared services)
- ✅ Accurate complexity from actual code, not assumptions
- ✅ Engineers trust estimates (based on code they wrote)
- ✅ Fewer "we didn't know it touches X" surprises mid-sprint

**Example:**

*Without scanning*: "Add PDF export" → 8 points (guess)

*With scanning*: Claude reveals it needs Indica service + S3 + background jobs → Break down into 4 stories (14 points realistic)

**Use when**: Technical features, service integrations, database changes.

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
