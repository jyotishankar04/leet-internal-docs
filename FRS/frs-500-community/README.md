# FRS-500 — Community

### Purpose

The Community module enables users to publish, discover, discuss, evaluate, collaborate on, and moderate programming problems and related content.

It provides the social layer of the platform while ensuring content quality and healthy community interactions.

## Scope

```
Community
│
├── Community Feed
├── Public Problems
├── Comments
├── Replies
├── Reactions
├── Bookmarks
├── Shares
├── Reports
├── Problem Reviews
├── Discussions
├── Following (Future)
├── Collections
├── Trending
├── Reputation
└── Moderation
```

## Community Content

The platform supports multiple community objects.

Initially:

* Problems
* Comments
* Reviews

Future:

* Articles
* Playlists
* Roadmaps
* Tutorials
* Contests

The community module should be extensible enough to support these later.





### Community Module Summary

| Category             | Requirements           |
| -------------------- | ---------------------- |
| Publishing           | FR-501                 |
| Discovery            | FR-502, FR-503, FR-520 |
| Engagement           | FR-504 – FR-510        |
| Moderation           | FR-511, FR-515, FR-516 |
| Reviews              | FR-512                 |
| Reputation           | FR-513                 |
| Discovery Algorithms | FR-514                 |
| Collections          | FR-517                 |
| Creator Tools        | FR-518                 |
| Social Graph         | FR-519                 |

## Architectural Observations

This module introduces several important concepts that will shape the backend:

#### 1. Community Feed

The feed is **not** just a database query. Over time it may use ranking algorithms, caching, and recommendation logic.

#### 2. Reputation

Reputation should be an independent subsystem rather than a simple integer on the `User` table. Every reputation change should be traceable.

#### 3. Reviews vs Comments

Keep these as separate domain concepts:

* **Comments** → discussions and questions.
* **Reviews** → structured evaluations with ratings and quality metrics.

#### 4. Collections

Collections should be generic enough to support future content types (problems, articles, roadmaps) rather than being tied only to problems.

#### 5. Moderation

Treat moderation as a first-class workflow with reports, review queues, and actions, rather than sprinkling moderation flags throughout different tables.
