# Requirements Breakdown Prompts

Turn 50-point stories into 3-8 point stories in 60 seconds.

## The Problem

Your user story takes 2-3 sprints instead of 1. Why?

It bundles 5+ features into 1 story.

## The Solution

Copy-paste prompts for AI-assisted story breakdown.

## Who This Is For

**Primary audience**: Product Owners without technical background

These prompts translate technical complexity into simple terms so you can create realistic stories without needing to understand code.

**Can also be used by**:
- Software Engineers (breaking down their own work)
- QA Engineers (understanding test scope)
- Technical Product Owners (with codebase knowledge)

But the focus is on **non-technical Product Owners** who need to plan technical features accurately.

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
2. **Use [Prompt 3: Scan Codebase](prompts/3-scan-codebase-for-context.md)** to get non-technical overview
   - AI scans actual code files (no guessing!)
   - Extracts key components, services, dependencies
   - Translates technical details into simple terms
   - Outputs actionable breakdown points
3. **Copy context from AI's findings**
4. **Use [Prompt 1: Break Down](prompts/1-break-down-large-story.md)** with technical context
5. **Get realistic breakdown** based on real architecture

**Why codebase scanning matters:**
- ✅ **Eliminates AI hallucination** - AI reads actual code, doesn't guess
- ✅ Discovers hidden dependencies (3rd party APIs, shared services)
- ✅ Accurate complexity from actual code, not assumptions
- ✅ Engineers trust estimates (based on code they wrote)
- ✅ Fewer "we didn't know it touches X" surprises mid-sprint

**Use when**: Technical features, service integrations, database changes.

## Real Example

**Before**: 1 story, 50 points, took 6 weeks

**After**: 10 stories, 48 points total, delivered in 6 weeks (on time)

[See the complete breakdown →](examples/story-breakdown-example.md)

## Available Prompts

- **[Break Down Large Story](prompts/1-break-down-large-story.md)** → Story is too large or bundles multiple features
- **[Rewrite Correct Format](prompts/2-rewrite-correct-format.md)** → Story is unclear
- **[Scan Codebase for Context](prompts/3-scan-codebase-for-context.md)** → Understand existing implementation (use with Claude Code)

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

## Contributing

Have a recurring problem that needs a prompt solution? We want to hear about it!

**Suggest a new prompt**:
1. [File an issue](../../issues/new/choose) using the "Prompt Idea" template
2. Describe your problem and how often you face it
3. If it's recurring (not a one-time issue), we'll create a prompt

**Improve existing prompts**: Submit a Pull Request with before/after examples

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidelines.

**Why frequency matters?** One-time problems don't need prompts. We focus on recurring pain points.

## License

[MIT](LICENSE)
