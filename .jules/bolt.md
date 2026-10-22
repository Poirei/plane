## 2024-05-14 - [Backend Multiple Counts Optimization]
**Learning:** In Django backend views, performing multiple `.count()` calls on the same base queryset but with different `.filter()` arguments is an N+1 query problem that degrades performance due to multiple database round trips.
**Action:** Always combine multiple `.count()` calls into a single database query using Django's `.aggregate()` function combined with `Count` and `filter=Q(...)` (e.g., `Count("id", filter=Q(state__group="completed"), distinct=True)`).
