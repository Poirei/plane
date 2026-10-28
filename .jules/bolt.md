
## 2024-05-20 - [Combine multiple Count queries using Django Aggregate]
**Learning:** In Django views that return dashboard statistics, multiple `.count()` queries on the same table can cause significant database load and latency due to repetitive round-trips.
**Action:** When calculating several counts on the same model with different filters, combine them into a single query using Django's `.aggregate()` and `Count(..., filter=..., distinct=True)`. Always restrict the base `.filter()` using `Q` objects to avoid unintentionally widening the scope across the entire table before aggregation.
