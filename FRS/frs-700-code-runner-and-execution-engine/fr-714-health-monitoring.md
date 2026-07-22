# FR-714 — Health Monitoring

Each worker shall periodically report:

* CPU
* Memory
* Queue length
* Active jobs
* Last heartbeat

Unhealthy workers shall stop receiving new jobs.
