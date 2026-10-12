## 2024-05-24 - Avoid Django deepcopy() on querysets
**Learning:** Found an anti-pattern where `copy.deepcopy(queryset)` was used to clone a Django queryset to obtain counts and annotations separately. This is highly inefficient as it tries to copy the entire object graph recursively.
**Action:** Always use `.all()` to clone querysets which avoids Python-level deepcopy while securely preventing the modified clone from affecting the original queryset's constraints.
