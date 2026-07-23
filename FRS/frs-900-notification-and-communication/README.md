# FRS-900 — Notification & Communication

## Purpose

The Notification module delivers timely, relevant, and configurable notifications to users across multiple channels.

It is responsible for **notification generation**, **delivery**, **user preferences**, and **notification history**.

> **Important Boundary**
>
> This module **does not decide business logic**.
>
> Other modules generate events.
>
> Notification only decides **how**, **when**, and **where** to notify users.

#### Scope

```
Notification
│
├── In-App Notifications
├── Email Notifications
├── Push Notifications (Future)
├── Notification Preferences
├── Notification History
├── Read / Unread
├── Batching
├── Scheduling
├── Templates
└── Delivery Status
```

***

## Notification Flow

```
Domain Event
      │
      ▼
Notification Service
      │
      ▼
Create Notification
      │
      ▼
Choose Channels
      │
      ▼
Deliver
      │
      ▼
Store History
```

## Notification Types

Initially:

* Problem Published
* Problem Approved
* Problem Rejected
* Appeal Decision
* AI Generation Complete
* Submission Finished
* Comment Reply
* Mention
* Review Received
* Badge Earned
* Weekly Summary

Future:

* Contest
* Job Alerts
* Roadmap Updates

## Module Summary

| Category    | Requirements |
| ----------- | ------------ |
| Creation    | FR-901       |
| Delivery    | FR-902–903   |
| Preferences | FR-904       |
| Management  | FR-905–906   |
| Templates   | FR-907       |
| Scheduling  | FR-908–909   |
| Reliability | FR-910–911   |
| Lifecycle   | FR-912       |
| Social      | FR-913       |
| Security    | FR-914       |
| Analytics   | FR-915       |

***

## Architectural Observations

### 1. Event-Driven by Design

Notifications should subscribe to domain events such as:

```
SubmissionCompleted
CommentCreated
ProblemPublished
ProblemPromoted
AppealResolved
ReviewReceived
```

The originating service should never call the notification service directly.

***

### 2. Multi-Channel Delivery

Keep delivery adapters separate:

```
Notification
        │
        ├── In-App
        ├── Email
        └── Push
```

Adding SMS or Discord later should not require changing business logic.

***

### 3. Template-Based Messages

Avoid hardcoded notification text. Use versioned templates with placeholders (e.g., `{problemName}`, `{creatorName}`) to simplify localization and maintenance.

***

### 4. Reliable Delivery

Use background jobs for email and scheduled notifications. If the provider is temporarily unavailable, retries and dead-letter handling should be part of the delivery pipeline.

***

### 5. User-Controlled Experience

Every non-essential notification should respect user preferences. Transactional notifications (password reset, security alerts, email verification) should bypass preference settings because they are required for account integrity.

***

### Design Recommendation for LeetSocial

Rather than treating notifications as isolated messages, model them around **Domain Events**.

For example:

```
ProblemPublished
        │
        ├── Notify followers
        ├── Update creator activity
        ├── Trigger search indexing
        ├── Recalculate trending
        └── Queue emails (if enabled)
```

This makes notifications just one consumer of events alongside analytics, search, and recommendations. It keeps the platform loosely coupled and easier to evolve.
