# S8 Architecture Review – Team Tech Ninjas

## Outgoing review (what we wrote about another team)

**Strong**

* Their context diagram was easy to read and clearly showed the external systems.
* Error handling was consistent across their main endpoints

**Risk**

* Performance NFR was mentioned but there was no clear test plan yet.
* Some components in the diagram had many responsibilities mixed together.

**Question**

* How do they plan to monitor the system in production (logs, metrics, uptime, etc.)?

---

## Inbound feedback (what another team told us)

**Strong**

* Good separation between web UI, API and domain services.
* The NFR mapping table is readable and connects to the endpoints.

**Risk**

* No real performance test yet, only the idea to add one later.
* The availability NFR is not linked to any concrete alerting or dashboard.

**Question**

* Could we move some logic from the API Gateway into separate services later if the project grows?

---

## What we will adjust

* Add a small section about indexing and basic monitoring in `tradeoffs.md`.
* Make sure our `/v1/dashboard` endpoint is part of a simple uptime check.
* When we have more time, add a small k6 script for the courses API (T‑PERF‑01).
