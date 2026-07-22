---
description: The system shall authenticate registered users.
---

# FR-102 Login

#### Priority

Critical

#### Actors

* Registered User

#### Preconditions

* Account exists.
* Account is active.

#### Main Flow

1. User enters credentials.
2. System validates credentials.
3. Access token is issued.
4. Refresh token is issued.
5. Session is recorded.

#### Alternative Flows

* Invalid credentials.
* Locked account.
* Unverified email.

#### Postconditions

* User is authenticated.

#### Acceptance Criteria

* Valid credentials return tokens.
* Invalid credentials are rejected.
* Sessions are securely created.
