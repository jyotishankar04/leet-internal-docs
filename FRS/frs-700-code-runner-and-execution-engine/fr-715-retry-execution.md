---
description: >-
  If execution fails due to infrastructure issues (not user code), the platform
  may retry the job.
---

# FR-715 — Retry Execution

Retries must not occur for:

* Compilation Error
* Wrong Answer
* Runtime Error caused by user code
