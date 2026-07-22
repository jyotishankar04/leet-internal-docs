# FR-550 — Problem Quality & Trust

Instead of deciding promotion based only on manual review, reviewers receive a **quality report**.

## Why?

Today platforms rely on:

* Likes
* Views
* Downloads

These are popularity metrics.

Popularity ≠ Quality.

Example:

Problem A

* 500 likes
* Wrong constraints
* Weak test cases

Problem B

* 30 likes
* Excellent statement
* Excellent hidden tests
* Great editorial

Which deserves Official?

Problem B.

***

## Quality Score

Instead of one score

```
Quality Score87/100
```

We'll build multiple scores.

***

### 1. Technical Quality

Measures

* Correct constraints
* Test case coverage
* Reference solution correctness
* Complexity accuracy
* Boilerplate validity

***

### 2. Community Quality

Measures

* Reviews
* Likes
* Solve rate
* Comment quality
* Duplicate reports

***

### 3. Difficulty Confidence

Example

```
Creator says
Hard
Community says
Easy
Acceptance
95%
System estimates
Easy
↓
Flag inconsistency.
```

***

### 4. Originality Score

AI + embeddings detect

* Exact duplicates
* Near duplicates
* Same algorithm
* Same idea
* Same constraints

Example

```
Two Sum Similarity 98% Originality Low
```

***

### 5. Stability Score

Measures

How often the problem changes.

Too many edits

↓

Low stability.

Official problems should rarely change.

***

### 6. Trust Score

Based on creator history.

Example

```
Creator
Problems Published
42
Official Problems
10
Rejected
1
Reports
0
Average Rating
4.8
Trust
97%
Another
Problems
15
Rejected
12
Spam
4
Trust
18%
```





## Problem Quality Pipeline

```
Draft
   │
   ▼
Validation
   │
   ▼
AI Quality Check
   │
   ▼
Duplicate Detection
   │
   ▼
Community Publication
   │
   ▼
Community Feedback
   │
   ▼
Quality Calculation
   │
   ▼
Reviewer Dashboard
   │
   ▼
Official Recommendation
```
