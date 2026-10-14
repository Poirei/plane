## 2023-10-14 - [Combine multiple Count queries using aggregate]
**Learning:** The Plane codebase uses Django's ORM in its backend. In several analytics/dashboard endpoints, multiple `.count()` queries are executed sequentially against the same base queryset to get different metrics (e.g., total assigned, pending, completed). This causes an N+1 query performance bottleneck.
**Action:** Use Django's `.aggregate()` function combined with conditional `Count(..., filter=...)` to reduce multiple `.count()` calls into a single database query. This drastically reduces round-trip latency.
