---
description: The runner shall accept execution jobs from trusted internal services.
---

# FR-701 — Accept Execution Job

A job contains:

* Submission ID
* Language
* User code
* Problem package reference
* Limits (time, memory, output)

The runner must not trust user input directly.
