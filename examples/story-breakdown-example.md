# Story Breakdown Example: Before & After

Real project example showing transformation from 1 large story (50+ points) to 10 shippable stories (48 points total).

---

## BEFORE: Bad Story (50+ Points)

### Original User Story

**Title**: Automatic Document Type Detection

**User Story**:
As a user uploading files, I want the system to automatically detect document type and metadata, So that I don't have to manually fill in these fields.

**Acceptance Criteria** (9 ACs):

1. System integrates with AI API for self-issued detection (issued vs received)
2. System integrates with AI API for document type classification (invoice, receipt, contract, etc.)
3. When "Auto-detect" checkbox is ON, system calls both APIs automatically
4. UI displays "Auto-detected: [value]" for detected fields
5. User can override auto-detected values before submitting
6. If confidence < 70%, system shows blank field or default value
7. System triggers OCR automatically for invoices and receipts
8. Retry logic with exponential backoff for temporary API failures (max 5 minutes)
9. Non-retryable errors (422) show user-friendly error message

### Why This is Bad

**Problem 1: Too Large (50+ Points)**

This story contains **5 distinct features**:
- Feature 1: AI API integration for self-issued detection (8 pts)
- Feature 2: AI API integration for document type classification (8 pts)
- Feature 3: UI auto-detection display + user override (8 pts)
- Feature 4: OCR trigger logic (5 pts)
- Feature 5: Error handling for both APIs (8 pts)

**Total**: 37-40 points = **2-3 sprints of work**, not 1 story

**Problem 2: Too Many Acceptance Criteria (9 ACs)**

Rule: Maximum 3-5 ACs per story. This has 9 ACs mixing multiple features.

**Problem 3: Bundled Implementation Details**

ACs mention "exponential backoff", "confidence < 70%", "422 errors" - these are HOW, not WHAT.

### Impact

**Timeline Risk**:
- Expected: 1 sprint (2 weeks)
- Reality: 2-3 sprints (4-6 weeks)
- **Deadline missed by 2-4 weeks**

**Team Confusion**:
- Engineers don't know what to implement first
- QA engineer can't test 9 ACs atomically
- Product owner can't track progress (stuck at "in progress" for weeks)

---

## AFTER: Good Stories (10 Stories, 48 Points)

### Transformation Result

**Before**: 1 story, 50+ points, 9 ACs
**After**: 10 stories, 3-8 points each, 3-5 ACs per story
**Timeline**: Fits in 3 sprints (March 16, 2026 deadline met)

---

### Sprint 1: API Foundation (16 points)

#### Story 2.1A: Self-Issued AI API Client (5 pts)
**User Story**: As an engineer, I want to call the AI API for self-issued detection, So that the system can predict if a document is "issued" or "received"

**ACs**:
1. API call returns prediction (issued/received) with confidence score
2. Authentication works with API key
3. Tests pass for both prediction types

---

#### Story 2.1B: Self-Issued API Error Handling (3 pts)
**User Story**: As an engineer, I want the AI API client to handle errors, So that server errors retry and client errors don't

**ACs**:
1. Server errors (500) retry automatically
2. Client errors (422) don't retry
3. Timeouts retry automatically

---

#### Story 2.2A: Document Type AI API Client (5 pts)
**User Story**: As an engineer, I want to call the AI API for document type classification, So that the system can predict document types (invoice, receipt, contract, etc.)

**ACs**:
1. API call returns document type prediction with confidence score
2. All 9 document types supported (invoice, receipt, quote, delivery, contract, purchase order, order confirmation, inspection document, others)
3. Tests pass for all document types

---

#### Story 2.2B: Document Type API Error Handling (3 pts)
**User Story**: As an engineer, I want the AI API client to handle errors, So that the system handles failures gracefully

**ACs**:
1. Server errors (500) retry automatically
2. Client errors (422) don't retry
3. Timeouts retry automatically

---

### Sprint 2: User-Facing Features (24 points)

#### Story 2.3: Auto-Detect Self-Issued (8 pts)
**User Story**: As a user uploading files, I want the system to auto-detect if the document is "issued" or "received", So that I don't have to select it manually

**ACs**:
1. When "Auto-detect" is ON, field shows "Auto-detected: Issued" or "Received"
2. User can override the auto-detected value
3. When "Auto-detect" is OFF, field is blank (manual selection required)
4. High confidence (≥70%) shows prediction
5. Low confidence (<70%) shows blank with help text

---

#### Story 2.4: Auto-Detect Document Type (8 pts)
**User Story**: As a user uploading files, I want the system to auto-detect document type, So that I don't have to select it manually

**ACs**:
1. When "Auto-detect" is ON, field shows "Auto-detected: [document type]"
2. All 9 document types supported
3. User can override the auto-detected value
4. High confidence (≥70%) shows prediction
5. Low confidence (<70%) defaults to "Others" with help text

---

#### Story 2.5: Trigger OCR for Auto-Detected Invoice/Receipt (5 pts)
**User Story**: As a user uploading an invoice or receipt, I want transaction details extracted automatically, So that I don't have to enter them manually

**ACs**:
1. OCR triggers for invoice and receipt types only
2. No OCR for other document types (contract, quote, etc.)
3. OCR respects manual override (if user changed type, respect that)
4. System uses correct OCR processing based on document type + self-issued combination

---

#### Story 2.6: Move "Auto-detect" Checkbox to Top (3 pts)
**User Story**: As a user uploading files, I want the "Auto-detect" checkbox at the top, So that I can easily toggle it before selecting files

**ACs**:
1. Checkbox is the first element at the top of the panel
2. Visual design matches Figma mockup
3. Functionality unchanged (auto-detection still works)

---

### Sprint 3: Error Handling Polish (8 points)

#### Story 2.7: Retry-Eligible Errors (5 pts)
**User Story**: As a user uploading files, I want the system to retry AI API calls when temporary errors occur, So that my upload succeeds even if the AI service is temporarily down

**ACs**:
1. System retries automatically on server errors (500) and timeouts with exponential backoff
2. Retry stops after 5 minutes total duration
3. File upload succeeds even during retry (non-blocking)
4. If retry fails, fields show blank and I can edit manually

---

#### Story 2.8: Non-Retry-Eligible Errors (3 pts)
**User Story**: As a user uploading files, I want to see a clear error message when the AI cannot process my file, So that I understand why auto-detection failed

**ACs**:
1. Client errors (422) don't retry
2. File upload still succeeds
3. Error message shows: "Failed to auto-detect for 3 files due to unsupported format"

---

## What Improved

**Timeline**: 48 points across 3 sprints = 16 points/sprint average
**Result**: Delivered on March 16, 2026 deadline (3 months)
**Team Velocity**: Predictable progress, no surprises

**Key Success Factors**:
- ✅ Each story is independently testable
- ✅ QA engineer can test 3-5 ACs per story (manageable)
- ✅ Product owner can track progress story-by-story
- ✅ Team can parallelize work (APIs in Sprint 1, UI in Sprint 2)
- ✅ No "stuck at in progress for weeks" - clear incremental progress
