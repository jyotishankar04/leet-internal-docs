# FRS-400 — AI Problem Studio

### Purpose

The AI Problem Studio enables users to create, refine, validate, and improve programming problems through natural language conversations.

It acts as an intelligent assistant throughout the problem authoring lifecycle.



#### Scope

```
AI Problem Studio
│
├── Prompt Understanding
├── Requirement Clarification
├── Planning
├── Duplicate Detection
├── Problem Generation
├── Conversational Editing
├── Validation
├── Difficulty Estimation
├── Test Case Generation
├── Starter Code Generation
├── Editorial Generation
├── Hint Generation
├── Reference Solution Generation
├── Similar Problem Discovery
└── AI Session History
```

## AI Workflow

Instead of immediately generating a problem, the system follows a workflow.

```
User Prompt
      │
      ▼
Requirement Analysis
      │
      ▼
Clarification Questions
      │
      ▼
Duplicate Detection
      │
      ▼
Generation Plan
      │
      ▼
Problem Generation
      │
      ▼
Validation
      │
      ▼
Create Draft
      │
      ▼
Chat-based Refinement
```

Notice that **generation is only one step**.



## AI Module Summary

| Category             | Requirements           |
| -------------------- | ---------------------- |
| Session Management   | FR-401, FR-405, FR-416 |
| Prompt Understanding | FR-402, FR-403, FR-404 |
| Duplicate Detection  | FR-406                 |
| Content Generation   | FR-407 – FR-412        |
| Editing              | FR-413, FR-414, FR-417 |
| Validation           | FR-415                 |
| Persistence          | FR-418                 |
| Analytics            | FR-419                 |
| Recovery             | FR-420                 |

## Design Principles

This module is built around a few key principles:

1. **AI assists, users decide.** The user always has final control over the generated content.
2. **Every AI-generated problem becomes a normal draft.** Once created, it follows the same lifecycle as a manually authored problem.
3. **Conversation is persistent.** AI interactions are part of the authoring history.
4. **Generation is modular.** Users can regenerate or edit individual sections instead of restarting the entire process.
5. **Duplicate prevention is proactive.** Existing community knowledge is surfaced before creating near-identical problems.
