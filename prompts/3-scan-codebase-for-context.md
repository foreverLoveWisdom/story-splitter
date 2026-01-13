# Prompt 3: Scan Codebase for Story Context

**Purpose**: Get non-technical overview of how a feature currently works by having AI scan actual code.

**Use this prompt in**: [Claude Code](https://claude.ai/code) terminal (in your codebase directory)

---

## The Prompt

```
I'm a Product Owner planning a new feature related to [FEATURE NAME].

I need to understand how [FEATURE NAME] currently works in this codebase, but WITHOUT technical jargon.

Please:

1. **SCAN THE ACTUAL CODE** (use grep, read files, search directories - don't guess!)
2. Find all files/components related to [FEATURE NAME]
3. Read the code to understand what it does
4. Explain to me in simple terms:
   - What does this feature currently do? (user perspective)
   - What external services does it use? (API names, not code details)
   - What database tables store its data? (table names only)
   - What background jobs/async work happens? (job names, what triggers them)
   - What other features depend on this? (connected features)

5. **Turn findings into actionable points**:
   - If I want to add [NEW FUNCTIONALITY], what parts need to change?
   - What new components would I need to create?
   - What are the biggest technical risks?

6. **Format your answer like this**:

## Current Implementation (Simple Terms)

[Explain what code does from user perspective]

## Key Components

- **Service A**: [What it does]
- **Database Table X**: [What data it stores]
- **Background Job Y**: [When it runs, what it does]

## Dependencies

[What other features/systems this connects to]

## To Add [NEW FUNCTIONALITY], You Need:

- [ ] Story 1: [Actionable change]
- [ ] Story 2: [Actionable change]
- [ ] Story 3: [Actionable change]

## Technical Risks

[What could go wrong, in simple terms]

---

**CRITICAL**: Base your answer ONLY on code you actually read. If you can't find something in the code, say "I couldn't find [X] in the codebase" - don't guess!
```

---

## Example Usage

**Context**: You're planning to add "PDF export with digital signature" feature

**What you paste into Claude Code**:

```
I'm a Product Owner planning a new feature related to PDF generation.

I need to understand how PDF generation currently works in this codebase, but WITHOUT technical jargon.

[... rest of prompt ...]
```

**What Claude Code does**:
1. Scans codebase with `grep`, reads actual files
2. Finds: `app/services/pdf_generator.rb`, `lib/indica/client.rb`, `app/jobs/pdf_processing_job.rb`
3. Reads the code
4. Explains in simple terms

**What you get back**:

```
## Current Implementation (Simple Terms)

When a user uploads a document, the system converts it to PDF using an external service called "Indica". The PDF is stored in S3 cloud storage and a background job processes it asynchronously.

## Key Components

- **Indica Service**: External API that converts files to PDF format
- **coffret_files table**: Stores file metadata (name, size, upload date)
- **S3 Storage**: Where actual PDF files are stored
- **PdfProcessingJob**: Runs in background after upload completes

## Dependencies

- Cloud Expense product uploads 47% of all files
- Invoice product also uses this for receipt processing

## To Add "PDF Digital Signature", You Need:

- [ ] Story 1: Integrate with signature service API
- [ ] Story 2: Add signature verification button to UI
- [ ] Story 3: Store signature metadata in database
- [ ] Story 4: Update PdfProcessingJob to handle signatures

## Technical Risks

- Indica service doesn't support signatures yet (need to check with team)
- Existing PDFs won't have signatures (need migration plan)
```

---

## Why This Works

**Eliminates hallucination**:
- ✅ AI must scan actual code files (forced verification)
- ✅ You see which files it read (transparency)
- ✅ If code doesn't exist, AI says so (no guessing)

**Product Owner friendly**:
- ✅ No code snippets, just concepts
- ✅ Focuses on "what" not "how"
- ✅ Actionable breakdown points
- ✅ Highlights risks before sprint starts

**Saves time**:
- ✅ No need to ask engineers "how does X work?"
- ✅ Faster story creation with accurate context
- ✅ Fewer surprises during implementation

---

## When to Use This

- ✅ **Before sprint planning** - Understand existing system
- ✅ **Modifying existing features** - See what's already there
- ✅ **Technical features** - Service integrations, database changes
- ✅ **Legacy features** - No one remembers how it works

## When NOT to Use This

- ❌ **Brand new features** - No existing code to scan
- ❌ **Pure UI changes** - No backend complexity
- ❌ **No codebase access** - Use Prompt 1 instead
