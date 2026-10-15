## 2024-10-15 - Django Query Optimization in WorkspaceUserProfileStatsEndpoint
**Learning:** Found an N+1 query or multiple separate .count() queries pattern in `apps/api/plane/app/views/workspace/user.py`. `WorkspaceUserProfileStatsEndpoint` does 4 separate queries to count created, assigned, pending, and completed issues.
**Action:** Replace multiple `.count()` queries with a single query using Django `.aggregate()` and `Count(..., filter=...)` to reduce database round-trips as per our instructions for backend database query optimization.
