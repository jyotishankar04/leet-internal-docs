# FRS-800 — Search & Discovery

## Purpose

The Search & Discovery module enables users to efficiently discover problems, creators, collections, discussions, and future content through keyword search, filters, recommendations, and intelligent ranking.

The module shall provide both **traditional search** and **AI-assisted semantic discovery**.

#### Scope

```
Search & Discovery
│
├── Keyword Search
├── Problem Search
├── Creator Search
├── Tag Search
├── Collection Search
├── Filters
├── Sorting
├── Recommendations
├── Trending
├── Similar Problems
├── AI Semantic Search
└── Search Analytics
```

## Searchable Content

Initially:

* Problems
* Creators
* Tags
* Collections

Future:

* Editorials
* Discussions
* Articles
* Tutorials
* Roadmaps
* Contests

The search engine should be designed so new content types can be indexed without redesigning the module.

## Module Summary

| Category        | Requirements |
| --------------- | ------------ |
| Search          | FR-801–805   |
| Filtering       | FR-806–810   |
| Recommendations | FR-811–815   |
| Analytics       | FR-817       |
| Indexing        | FR-818       |
| Security        | FR-819       |
| API             | FR-820       |

## Architectural Observations

### 1. Search Engine ≠ Database

Don't use PostgreSQL as your primary search engine beyond simple lookups.

Instead, define an abstract **Search Index**. Today it might be Meilisearch or PostgreSQL full-text search; tomorrow it could be Elasticsearch or OpenSearch. The rest of the platform shouldn't care.

***

### 2. Event-Driven Indexing

The Search module should **never poll the database**.

Instead, listen for domain events such as:

```
ProblemPublishedProblemUpdatedProblemArchivedCollectionCreatedCreatorUpdated
```

Each event updates the search index asynchronously.

***

### 3. Ranking Pipeline

Search results should be ranked by more than text relevance. A future ranking pipeline can combine:

```
Final Score =Text Relevance+ Quality Score+ Personalization+ Trending Boost+ Freshness
```

This keeps search useful even as the platform grows.

***

### 4. AI Semantic Search

Treat semantic search as an enhancement, not a replacement.

A good hybrid flow is:

```
User Query      │      ├── Keyword Search      └── Semantic Embedding Search               │               ▼        Merge & Re-rank Results               │               ▼          Return Final Results
```

This gives precise matches for exact terms while still handling natural-language queries.

***

### 5. Search as a Cross-Cutting Capability

Search should eventually index more than problems. Design the index around a generic **Searchable Content** model so future modules (articles, tutorials, roadmaps, discussions, contests) can plug in without rewriting the search system.
