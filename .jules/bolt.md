## 2026-10-18 - Optimize Database Round-Trips for State Queries
**Learning:** In Django endpoints calculating aggregates for various states (like cycles progress), making separate `.count()` queries per state is an anti-pattern causing N+1/multiple query problems. Using `.aggregate()` with conditional `Count` operations (e.g. `Count('id', filter=Q(...))`) is much more efficient.
**Action:** Always scan for repeated `.count()` calls on the same base queryset. Combine them using `.aggregate()` with conditional filters instead.
