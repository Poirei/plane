## 2024-05-18 - [Combine Django counts into single aggregate]
**Learning:** Multiple sequential `.count()` calls in Django can be a major source of N+1 (or 1+N) query issues.
**Action:** Always replace multiple `.count()` calls on the same model with a single base `.filter(...)` followed by an `.aggregate(name=Count('id', filter=Q(condition), distinct=True))` to hit the DB only once. Ensure the base `.filter(...)` is appropriately restrictive to prevent scanning the entire table.
