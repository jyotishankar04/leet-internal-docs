# FR-713 — Worker Pool

The runner shall maintain a pool of execution workers.

Workers may be:

* Idle
* Busy
* Offline
* Draining
* Failed

Workers execute one job at a time.
