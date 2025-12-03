# Interfaces – Tech Ninjas API (draft)

Below we describe a few important endpoints. This is focused on *what* they do, not *how* we implement them.

---

## 1. List courses

- **Resource**: Courses  
- **Method**: `GET /v1/courses`  
- **Auth**: Bearer token, scope `courses:read`  
- **Request**
  - Query params:
    - `cursor` (string, optional)
    - `limit` (int, optional, default 25, max 100)
- **200 response**
  - JSON body:
    ```json
    {
      "items": [
        { "id": "c1", "title": "Intro to Python", "level": "beginner" }
      ],
      "nextCursor": "abc123"
    }
    ```
- **4xx/5xx**
  - `401` if token missing or invalid  
  - `403` if user has no access  
  - `429` if rate limit exceeded (retry is allowed)  
  - `500` for unexpected server error  
  - Error shape:
    ```json
    {
      "error": {
        "code": "string",
        "message": "string",
        "details": {},
        "traceId": "string"
      }
    }
    ```
- **Pagination**
  - Cursor based. If `nextCursor` is null, there is no next page.
- **Idempotency**
  - Not needed for GET.
- **Versioning**
  - Path versioning: `/v1/...`. If we break something in the future, we would add `/v2/courses`.
- **Notes**
  - Used by dashboard to show the first screen of courses.

---

## 2. Get a single course

- **Method**: `GET /v1/courses/{courseId}`
- **Auth**: Bearer token, `courses:read`
- **Path param**: `courseId` (string)
- **200**: returns one course with id, title, description, level
- **404**: course not found (uses same error schema as above)
- **Other codes**: `401`, `403`, `500` similar to list.

---

## 3. Enrol student to course

- **Method**: `POST /v1/enrolments`
- **Auth**: Bearer token, `enrolments:write`
- **Headers**
  - `Idempotency-Key` (string, required)
- **Body**
  ```json
  {
    "courseId": "c1"
  }
  ```
- **201**: enrolment created
  ```json
  {
    "id": "e123",
    "courseId": "c1",
    "userId": "u456",
    "createdAt": "2025-11-05T12:00:00Z"
  }
  ```
- **4xx/5xx**
  - `400` invalid JSON or missing fields
  - `401`, `403` as usual
  - `409` user already enrolled in the course
  - `422` validation error (uses error schema from above)
  - `429` if rate limited (retryable)
  - `500` server error
- **Idempotency**
  - If a request is retried with the same `Idempotency-Key` within 1 hour, we return the same 201 body again.
- **Versioning**
  - Same as above: `/v1/enrolments`.

---

## 4. Dashboard summary

- **Method**: `GET /v1/dashboard`
- **Auth**: Bearer token, `dashboard:read`
- **Request**: no body, only authenticated user
- **200**: small summary (e.g. number of active courses, progress %)
- **SLO note**
  - p95 latency target `< 200 ms` for normal load (relates to NFR-PERF-01).
