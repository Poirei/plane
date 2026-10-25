
## 2025-02-25 - Batching Multiple DB Counts
**Learning:** When retrieving counts for multiple conditions on the same model in Django, doing separate `.count()` calls triggers multiple database roundtrips. We can batch them into a single `.aggregate()` call using `Count('id', distinct=True, filter=Q(...))`. This prevents duplicate counting on M2M relationships and drastically reduces roundtrips.
**Action:** Use `.aggregate()` with conditional `Count` (using `filter` and `distinct=True`) whenever you see multiple `.count()` calls executing back-to-back on the same base queryset.
