---
description: >-
  The Problem Management module enables users to create, manage, publish,
  version, discover, and maintain programming problems throughout their
  lifecycle.
---

# FRS-300 — Problem Management

### Purpose

The Problem Management module enables users to create, manage, publish, version, discover, and maintain programming problems throughout their lifecycle.

It supports manual authoring, AI-assisted creation, community publishing, moderation, and promotion to the official problem set.

#### Scope

```
Problem Management
│
├── Problem Lifecycle
├── Problem Metadata
├── Visibility
├── Draft Management
├── Versioning
├── Publishing
├── Forking
├── Duplication
├── Ownership
├── Appeals
├── Official Promotion
├── Difficulty
├── Tags
├── Constraints
├── Examples
├── Hints
├── Editorial
├── Test Cases
├── Starter Code
└── Reference Solutions
```

Notice that **AI generation is NOT part of this module**. AI is just another producer of problem drafts. This separation keeps the Problem domain independent of how a problem is created.

## Problem Module Summary

| Category   | Requirements    |
| ---------- | --------------- |
| Creation   | FR-301 – FR-305 |
| Visibility | FR-306          |
| Reuse      | FR-307 – FR-308 |
| Versioning | FR-309 – FR-310 |
| Moderation | FR-311 – FR-315 |
| Metadata   | FR-316 – FR-319 |
| Content    | FR-320 – FR-324 |
| Ownership  | FR-325          |
| Validation | FR-326          |
| Analytics  | FR-327          |

## Problem Lifecycle

```
Draft
│
▼
Private
│
▼
Community
│
▼
Appealed
│
▼
Under Review
│
▼
Official
│
▼
Archived
```

Every problem moves through defined states.

Rules:

* Every problem starts as a draft.
* Drafts are private.
* Publishing creates a community problem.
* Community problems can be appealed.
* Reviewers evaluate appealed problems.
* Approved problems become official.
* Archived problems remain visible but are read-only.
