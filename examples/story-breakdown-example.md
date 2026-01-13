# Story Breakdown Example: Before & After

Example showing transformation from 1 large story (50+ points) to 10 shippable stories (48 points total).

---

## BEFORE: Bad Story (50+ Points)

### Original User Story

**Title**: Email Notification System

**User Story**:
As a user, I want to receive email notifications about important events, So that I stay informed without checking the app constantly.

**Acceptance Criteria** (9 ACs):

1. System integrates with email service API for sending emails
2. System integrates with template service for email formatting
3. When user enables notifications, system sends emails automatically
4. UI displays notification preferences with toggle switches
5. User can choose notification frequency (instant, daily digest, weekly summary)
6. User can override default notification types
7. System queues emails in background job when user performs actions
8. Retry logic with exponential backoff for temporary API failures (max 5 minutes)
9. Non-retryable errors (invalid email) show user-friendly error message

### Why This is Bad

**Problem 1: Too Large (50+ Points)**

This story contains **5 distinct features**:
- Feature 1: Email service API integration (8 pts)
- Feature 2: Template service integration (8 pts)
- Feature 3: UI preferences panel + user settings (8 pts)
- Feature 4: Background job queue logic (5 pts)
- Feature 5: Error handling for both services (8 pts)

**Total**: 37-40 points = **2-3 sprints of work**, not 1 story

**Problem 2: Too Many Acceptance Criteria (9 ACs)**

Rule: Maximum 3-5 ACs per story. This has 9 ACs mixing multiple features.

**Problem 3: Bundled Implementation Details**

ACs mention "exponential backoff", "max 5 minutes", "invalid email errors" - these are HOW, not WHAT.

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
**Timeline**: Fits in 3 sprints

---

### Sprint 1: Service Integration (16 points)

#### Story 1.1: Email Service API Client (5 pts)
**User Story**: As an engineer, I want to call the email service API, So that the system can send emails

**ACs**:
1. API call sends email with recipient, subject, and body
2. Authentication works with API key
3. Tests pass for successful email sending

---

#### Story 1.2: Email Service Error Handling (3 pts)
**User Story**: As an engineer, I want the email API client to handle errors, So that server errors retry and client errors don't

**ACs**:
1. Server errors (500) retry automatically
2. Client errors (invalid email) don't retry
3. Timeouts retry automatically

---

#### Story 1.3: Template Service API Client (5 pts)
**User Story**: As an engineer, I want to call the template service, So that emails have consistent formatting

**ACs**:
1. API call formats email with template name and data
2. Returns formatted HTML email
3. Tests pass for all template types

---

#### Story 1.4: Template Service Error Handling (3 pts)
**User Story**: As an engineer, I want the template API client to handle errors, So that the system handles failures gracefully

**ACs**:
1. Server errors (500) retry automatically
2. Client errors (invalid template) don't retry
3. Timeouts retry automatically

---

### Sprint 2: User-Facing Features (24 points)

#### Story 2.1: Notification Preferences UI (8 pts)
**User Story**: As a user, I want to set my notification preferences, So that I control what emails I receive

**ACs**:
1. Preferences page shows toggle switches for each notification type
2. User can enable/disable notifications
3. Changes save immediately
4. Current settings display correctly on page load
5. Success message shows after saving

---

#### Story 2.2: Notification Frequency Selector (8 pts)
**User Story**: As a user, I want to choose how often I receive notifications, So that I'm not overwhelmed with emails

**ACs**:
1. Dropdown shows three options: Instant, Daily Digest, Weekly Summary
2. Selection applies to all enabled notification types
3. Default is "Instant" for new users
4. Changes save immediately
5. Current frequency displays correctly on page load

---

#### Story 2.3: Background Email Queue (5 pts)
**User Story**: As a user, I want emails sent in the background, So that my actions in the app aren't delayed

**ACs**:
1. Emails queue immediately when actions occur
2. App doesn't wait for email to send
3. Failed emails retry automatically
4. Users don't see errors if email fails

---

#### Story 2.4: Move Preferences Link to Settings Menu (3 pts)
**User Story**: As a user, I want easy access to notification settings, So that I can change preferences quickly

**ACs**:
1. "Notification Preferences" link appears in Settings menu
2. Link opens preferences page
3. Visual design matches other menu items

---

### Sprint 3: Error Handling Polish (8 points)

#### Story 3.1: Retry-Eligible Errors (5 pts)
**User Story**: As a user, I want the system to retry sending emails when temporary errors occur, So that I don't miss important notifications

**ACs**:
1. System retries automatically on server errors (500) and timeouts
2. Retry stops after 5 minutes total duration
3. User actions aren't blocked during retry
4. If retry fails, user doesn't see error (silent failure)

---

#### Story 3.2: Non-Retry-Eligible Errors (3 pts)
**User Story**: As a user with an invalid email address, I want to see a clear error message, So that I can fix my email

**ACs**:
1. Client errors (invalid email) don't retry
2. Error message shows: "Cannot send notifications - please update your email address"
3. Link to profile page where user can fix email

---

## What Improved

**Timeline**: 48 points across 3 sprints = 16 points/sprint average
**Result**: Delivered on deadline (3 months)
**Team Velocity**: Predictable progress, no surprises

**Key Success Factors**:
- ✅ Each story is independently testable
- ✅ QA engineer can test 3-5 ACs per story (manageable)
- ✅ Product owner can track progress story-by-story
- ✅ Team can parallelize work (APIs in Sprint 1, UI in Sprint 2)
- ✅ No "stuck at in progress for weeks" - clear incremental progress
