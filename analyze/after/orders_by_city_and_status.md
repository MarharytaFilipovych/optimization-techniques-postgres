| QUERY PLAN |
| :--- |
| Bitmap Heap Scan on orders  \(cost=288.37..1902.53 rows=17977 width=49\) \(actual time=1.573..12.464 rows=17463 loops=1\) |
|   Recheck Cond: \(status = 'paid'::text\) |
|   Filter: \(delivery\_city \~\~ '%a%'::text\) |
|   Rows Removed by Filter: 8281 |
|   Heap Blocks: exact=1231 |
|   -&gt;  Bitmap Index Scan on index\_orders\_status  \(cost=0.00..283.87 rows=25544 width=0\) \(actual time=1.308..1.308 rows=25753 loops=1\) |
|         Index Cond: \(status = 'paid'::text\) |
| Planning Time: 4.084 ms |
| Execution Time: 13.283 ms |
