---
description: The system shall allow a guest to register a new account.
---

# FR-101 User Registration

#### Priority

Critical

#### Actors

* Guest

#### Preconditions

* User is not authenticated.
* Email is not already registered.

#### Main Flow

1. User enters registration details.
2. System validates input.
3. System creates an inactive account.
4. System sends a verification email.
5. User verifies the email.
6. Account becomes active.

#### Alternative Flows

* Email already exists.
* Invalid email format.
* Weak password.
* Verification link expired.

#### Postconditions

* User account exists.
* Email is verified.
* User can log in.

#### Acceptance Criteria

* Duplicate emails are rejected.
* Password policy is enforced.
* Verification email is sent.
* User cannot log in before verification (configurable).
