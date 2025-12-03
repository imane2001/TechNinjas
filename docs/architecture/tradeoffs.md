## Context
NFR-PERF-01 states that our main course list and dashboard should remain responsive for normal use. At the same time, NFR-A11Y-01 demands that the dashboard be usable with basic accessibility tools and have zero critical WCAG2AA issues in an automated check. These two requirements drive both our architecture and implementation choices.

## Choice
We decided to keep a simple modular monolith. There is one backend application that exposes `/v1/courses` and `/v1/dashboard` and uses cursor pagination rather than large, heavy queries. On the frontend we strive to keep the dashboard light by using semantic HTML, minimal JavaScript and a small amount of client-side rendering.

## Alternatives Rejected
- **Full microservices split:** breaking the system into separate services for courses, progress and notifications adds complexity and deployment overhead that doesn’t pay off at our current size. For a student project this would slow us down without clear benefits.
- **Heavy single-page application:** relying entirely on a large JavaScript bundle would increase the initial load time and likely hurt our p95 latency on slower devices. By keeping most rendering server-side we reduce that risk.

## Risks & Mitigations
*Risk:* As the number of courses and students grows the dashboard queries could become slower.

*Mitigation:* Add indexes on fields we filter by most (such as `userId` and `status`), and consider introducing a simple cache in front of the `/v1/dashboard` endpoint if needed. We will also keep an eye on database query plans during development.

## Verification Hook
For S8 we run **T-A11Y-01** using `pa11y` on the dashboard page and store the resulting report at `evidence/EV-a11y-dashboard.html`. Later on, if time permits, we plan to add a small k6 script (T-PERF-01) to check the performance of the courses API under load.
