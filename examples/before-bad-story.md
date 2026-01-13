# Before: Bad Story Example (50+ Points)

## Original User Story 2 (from Real Project)

**Title**: Automatic Document Type Detection

**User Story**:
As a user uploading files, I want the system to automatically detect document type and metadata, So that I don't have to manually fill in these fields.

**Acceptance Criteria**:

1. System integrates with AI API for self-issued detection (issued vs received)
2. System integrates with AI API for document type classification (invoice, receipt, contract, etc.)
3. When "Auto-detect" checkbox is ON, system calls both APIs automatically
4. UI displays "Auto-detected: [value]" for detected fields
5. User can override auto-detected values before submitting
6. If confidence < 70%, system shows blank field or default value
7. System triggers OCR automatically for invoices and receipts
8. Retry logic with exponential backoff for temporary API failures (max 5 minutes)
9. Non-retryable errors (422) show user-friendly error message

---

## Why This is Bad

### Problem 1: Too Large (50+ Points)
This story contains **5 distinct features**:
- Feature 1: AI API integration for self-issued detection (8 pts)
- Feature 2: AI API integration for document type classification (8 pts)
- Feature 3: UI auto-detection display + user override (8 pts)
- Feature 4: OCR trigger logic (5 pts)
- Feature 5: Error handling for both APIs (8 pts)

**Total**: 37-40 points = **2-3 sprints of work**, not 1 story

### Problem 2: Too Many Acceptance Criteria (9 ACs)
Rule: Maximum 3-5 ACs per story. This has 9 ACs mixing multiple features.

### Problem 3: Bundled Implementation Details
ACs mention "exponential backoff", "confidence < 70%", "422 errors" - these are HOW, not WHAT.

---

## Impact

**Timeline Risk**:
- Expected: 1 sprint (2 weeks)
- Reality: 2-3 sprints (4-6 weeks)
- **Deadline missed by 2-4 weeks**

**Team Confusion**:
- Engineers don't know what to implement first
- QA engineer can't test 9 ACs atomically
- Product owner can't track progress (stuck at "in progress" for weeks)

---

## Solution

See [after-good-stories.md](./after-good-stories.md) for the correct breakdown (10 stories, 3-8 points each, 3-5 ACs per story).
