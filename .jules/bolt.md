
## $(date +%Y-%m-%d) - Combine multiple `.count()` queries with Django `.aggregate()`
**Learning:** In Django, when executing multiple independent `.count()` calls on the same model with different filters, each call executes a separate query, causing unnecessary database round trips.
**Action:** Combine these calls into a single query by using `.aggregate()` along with conditional `Count('id', filter=Q(...), distinct=True)`. Always restrict the base `.filter()` query as much as possible before aggregating to ensure the query remains highly performant and does not widen scope unintentionally.
