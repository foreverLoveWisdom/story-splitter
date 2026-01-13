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
1. Given I have email data, When I call the API, Then it sends the email with recipient, subject, and body
2. Given I have an API key, When I authenticate, Then the service accepts my request
3. Given the API call succeeds, When I run tests, Then all tests pass

---

#### Story 1.2: Email Service Error Handling (3 pts)
**User Story**: As an engineer, I want the email API client to handle errors, So that server errors retry and client errors don't

**ACs**:
1. Given server error (500) occurs, When API call fails, Then system retries automatically
2. Given client error (invalid email) occurs, When API call fails, Then system doesn't retry
3. Given timeout occurs, When API call fails, Then system retries automatically

---

#### Story 1.3: Template Service API Client (5 pts)
**User Story**: As an engineer, I want to call the template service, So that emails have consistent formatting

**ACs**:
1. Given template name and data, When I call the API, Then it formats the email
2. Given API call succeeds, When I receive response, Then it returns formatted HTML email
3. Given all template types, When I run tests, Then all tests pass

---

#### Story 1.4: Template Service Error Handling (3 pts)
**User Story**: As an engineer, I want the template API client to handle errors, So that the system handles failures gracefully

**ACs**:
1. Given server error (500) occurs, When API call fails, Then system retries automatically
2. Given client error (invalid template) occurs, When API call fails, Then system doesn't retry
3. Given timeout occurs, When API call fails, Then system retries automatically

---

### Sprint 2: User-Facing Features (24 points)

#### Story 2.1: Notification Preferences UI (8 pts)
**User Story**: As a user, I want to set my notification preferences, So that I control what emails I receive

**ACs**:
1. Given I open preferences page, When page loads, Then I see toggle switches for each notification type
2. Given I toggle a switch, When I change setting, Then notification enables/disables
3. Given I change settings, When I toggle, Then changes save immediately
4. Given I have saved settings, When page loads, Then current settings display correctly
5. Given I save changes, When save completes, Then success message shows

---

#### Story 2.2: Notification Frequency Selector (8 pts)
**User Story**: As a user, I want to choose how often I receive notifications, So that I'm not overwhelmed with emails

**ACs**:
1. Given I open frequency selector, When dropdown opens, Then I see three options: Instant, Daily Digest, Weekly Summary
2. Given I select frequency, When I choose option, Then selection applies to all enabled notification types
3. Given I'm a new user, When I first open page, Then default is "Instant"
4. Given I change frequency, When I select option, Then changes save immediately
5. Given I have saved frequency, When page loads, Then current frequency displays correctly

---

#### Story 2.3: Background Email Queue (5 pts)
**User Story**: As a user, I want emails sent in the background, So that my actions in the app aren't delayed

**ACs**:
1. Given I perform an action, When action completes, Then email queues immediately
2. Given email is queuing, When I perform action, Then app doesn't wait for email to send
3. Given email fails to send, When error occurs, Then system retries automatically
4. Given email fails permanently, When retry stops, Then I don't see error message

---

#### Story 2.4: Move Preferences Link to Settings Menu (3 pts)
**User Story**: As a user, I want easy access to notification settings, So that I can change preferences quickly

**ACs**:
1. Given I open Settings menu, When menu displays, Then "Notification Preferences" link appears
2. Given I click the link, When I click, Then preferences page opens
3. Given I view the menu item, When I see it, Then visual design matches other menu items

---

### Sprint 3: Error Handling Polish (8 points)

#### Story 3.1: Reliable Email Delivery (5 pts)
**User Story**: As a user, I want to receive notifications even when services are temporarily down, So that I don't miss important updates

**ACs**:
1. Given I enabled notifications, When temporary error occurs, Then I still receive the notification eventually
2. Given email is sending, When I use the app, Then my actions work normally without delays
3. Given temporary error happens, When I use the app, Then I don't see any error messages

---

#### Story 3.2: Invalid Email Address Warning (3 pts)
**User Story**: As a user with an invalid email address, I want to see a clear warning, So that I can fix my email and receive notifications

**ACs**:
1. Given my email is invalid, When I check notification settings, Then I see message: "Cannot send notifications - please update your email address"
2. Given I see the warning, When I click "Update Email", Then profile page opens
3. Given I fix my email, When I save, Then warning disappears

---

## What Improved

**Timeline**: 48 points across 3 sprints = 16 points/sprint average
**Result**: Delivered on deadline (3 months)
**Team Velocity**: Predictable progress, no surprises

**Key Success Factors**:
- ✅ Each story is independently testable
- ✅ QA engineer can test 3-5 ACs per story (manageable)
- ✅ Product owner can track progress story-by-story
- ✅ Team can parallelize work (backend and frontend engineers work simultaneously)
- ✅ No "stuck at in progress for weeks" - clear incremental progress
