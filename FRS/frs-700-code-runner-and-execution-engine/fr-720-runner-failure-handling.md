# FR-720 — Runner Failure Handling

The runner shall gracefully handle:

* Worker crashes
* Sandbox failures
* Compilation service failures
* Storage failures
* Queue interruptions

Failed jobs shall return standardized infrastructure errors.
