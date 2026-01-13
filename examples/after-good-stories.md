# After: Good Stories (10 Stories, 48 Points Total)

## Transformation Result

**Before**: 1 story, 50+ points, 9 ACs
**After**: 10 stories, 3-8 points each, 3-5 ACs per story
**Timeline**: Fits in 3 sprints (March 16, 2026 deadline met)

---

## Story Breakdown

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

## Impact

**Timeline**: 48 points across 3 sprints = 16 points/sprint average
**Result**: Delivered on March 16, 2026 deadline (3 months)
**Team Velocity**: Predictable progress, no surprises

**Key Success Factors**:
- Each story is independently testable
- QA engineer can test 3-5 ACs per story (manageable)
- Product owner can track progress story-by-story
- Team can parallelize work (APIs in Sprint 1, UI in Sprint 2)
