# FR-712 — Cleanup

After execution the runner shall:

* Kill processes
* Delete temporary files
* Destroy sandbox
* Release memory
* Return worker to pool

Cleanup must occur even if execution fails.
