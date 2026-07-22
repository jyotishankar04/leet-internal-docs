# FRS-600 — Submission & Judging

### Purpose

The Submission module is responsible for receiving user code, validating it, executing it through the runner, storing execution results, and maintaining submission history.

**Important Boundary**

This module **does not execute code**.

It only manages the **submission lifecycle**.

The **Code Runner (FR-700)** executes code.





#### Scope

```
Submission
│
├── Create Submission
├── Submission Queue
├── Submission History
├── Verdict
├── Runtime
├── Memory Usage
├── Language
├── Retry
├── Rejudge
├── Compare Submissions
├── Best Submission
├── Submission Analytics
└── Submission Status
```

#### Submission Lifecycle

```
Draft Code
     │
     ▼
Submit
     │
     ▼
Validation
     │
     ▼
Queued
     │
     ▼
Running
     │
     ▼
Judged
     │
     ▼
Stored
```

Every submission must follow this lifecycle.

#### Supported Verdicts

The platform shall support standardized verdicts.

```
Accepted

Wrong Answer

Compilation Error

Runtime Error

Time Limit Exceeded

Memory Limit Exceeded

Output Limit Exceeded

Presentation Error (optional)

Internal Error

Cancelled
```

These are platform-level verdicts.

Different runners may internally return different errors, but they must be normalized.



### Module Summary

| Category  | Requirements |
| --------- | ------------ |
| Creation  | FR-601–603   |
| Tracking  | FR-604       |
| Storage   | FR-605       |
| History   | FR-606–609   |
| Limits    | FR-610       |
| Rejudging | FR-611–613   |
| Analytics | FR-614       |
| Security  | FR-615–618   |
| Workflow  | FR-619–620   |

## Domain Principles

#### 1. Submissions are immutable.

Once created, a submission is never edited. Rejudging produces a new evaluation while preserving history.

#### 2. Submissions belong to a specific problem version.

If a problem evolves, old submissions remain tied to the exact version they were judged against.

#### 3. Submission management is separate from execution.

The Submission module handles lifecycle and persistence. The Code Runner module executes code in isolated environments.

#### 4. Every state transition is observable.

The platform should know when a submission was queued, picked up, started, finished, retried, or rejudged. This supports debugging, analytics, and operational monitoring.
