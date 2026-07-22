# SA-00

## Stakeholder Classificaiton

* Human Actors
* Internal System
* External System
* Platfrom Administrators



### &#x20;1. Human

The actual real users



#### 1.1 Guest

A visitor who has not registered.

#### Goals

* Explore the platform
* View official problems
* Browse community problems
* Search problems
* Register

#### Permissions

✅ View official problems

✅ View community problems

✅ Search public problems

❌ Submit code

❌ Create problems

❌ AI generation

❌ Comment

❌ Like

❌ Bookmark



### 1.2 Registered User

The base user role.

Every other user inherits from this.

#### Goals

* Solve problems
* Create problems
* Maintain private problem library
* Generate AI problems
* Publish problems
* Build profile

#### Permissions

Everything except administrative actions.



### 1.3 Problem Creator

A registered user actively creating content.

#### Goals

* Create problems
* Publish problems
* Use AI
* Maintain versions
* Appeal problems
* Build reputation

#### Permissions

* Create drafts
* Publish community problems
* Edit owned problems
* Delete owned drafts
* Appeal for official review



### 1.4 Problem Solver

Focuses on solving problems.

#### Goals

* Practice
* Track progress
* Improve ranking
* Save favorites
* View editorials

#### Permissions

* Submit code
* View submissions
* Bookmark
* Comment
* Like

## 2. Platform Staff

### 2.1 Reviewer

Technical reviewers responsible for content quality.

#### Responsibilities

Review appealed problems.

Approve.

Reject.

Provide feedback.

Maintain quality.

#### Permissions

* Access review queue
* Lock problems
* Approve
* Reject
* Return feedback
*

### 2.2 Administrator

Highest privilege.

#### Responsibilities

Platform management.

Moderation.

System configuration.

#### Permissions

Everything.





## 3. Internal System Actors

These are backend components.

***

### 3.1 AI Problem Studio

Responsibilities

* Generate problems
* Ask clarification
* Generate hints
* Generate editorial
* Duplicate detection
* Refine drafts

Consumes

Problem Prompt

Produces

Problem Draft

***

### 3.2 Submission Service

Responsibilities

Accept submissions.

Queue execution.

Store results.

***

### 3.3 Code Runner

Responsibilities

Compile.

Execute.

Judge.

Destroy containers.

Return verdict.

***

### 3.4 Search Service

Responsibilities

Index problems.

Index creators.

Provide search.

***

### 3.5 Notification Service

Responsibilities

Email.

In-app notifications.

Future push notifications.

***

### 3.6 Analytics Service

Responsibilities

Aggregate

Views

Attempts

Acceptance

Creator statistics

Trending



## 4. External Systems

***

### GitHub

Purpose

Push solved problems.

Sync repositories.

OAuth authentication (future).

***

### AI Provider

Examples

* OpenAI
* Gemini
* Anthropic

Purpose

LLM inference.

***

### Email Provider

Examples

* Resend
* SendGrid

Purpose

Verification.

Password reset.

Notifications.

***

### Object Storage

Examples

* Cloudflare R2
* AWS S3

Purpose

Store

Images

Attachments

Future datasets.



## Stakeholder Hierarchy

```
                      Guest
                        │
                 Register/Login
                        │
                        ▼
                Registered User
                 /             \
                /               \
      Problem Creator      Problem Solver
                \               /
                 \             /
                  ▼           ▼
                 Reviewer
                     │
                     ▼
              Administrator
```



## Permissions Matrix (High Level)

| Action                    | Guest | User | Creator | Reviewer | Admin |
| ------------------------- | ----- | ---- | ------- | -------- | ----- |
| View Official Problems    | ✅     | ✅    | ✅       | ✅        | ✅     |
| View Community Problems   | ✅     | ✅    | ✅       | ✅        | ✅     |
| Create Problem            | ❌     | ✅    | ✅       | ✅        | ✅     |
| Generate AI Problem       | ❌     | ✅    | ✅       | ✅        | ✅     |
| Publish Problem           | ❌     | ❌    | ✅       | ✅        | ✅     |
| Submit Code               | ❌     | ✅    | ✅       | ✅        | ✅     |
| Review Appeals            | ❌     | ❌    | ❌       | ✅        | ✅     |
| Manage Users              | ❌     | ❌    | ❌       | ❌        | ✅     |
| Approve Official Problems | ❌     | ❌    | ❌       | ✅        | ✅     |
