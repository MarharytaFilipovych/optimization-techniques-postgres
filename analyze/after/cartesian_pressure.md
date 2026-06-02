| QUERY PLAN |
| :--- |
| Aggregate  \(cost=3926.60..3926.61 rows=1 width=8\) \(actual time=70.087..70.090 rows=1 loops=1\) |
|   -&gt;  Hash Join  \(cost=756.65..3844.06 rows=33018 width=0\) \(actual time=7.934..67.673 rows=32732 loops=1\) |
|         Hash Cond: \(e.customer\_id = c.customer\_id\) |
|         -&gt;  Index Only Scan using index\_customer\_events\_wide\_time\_customer\_type on customer\_events\_wide e  \(cost=0.42..2957.46 rows=49659 width=4\) \(actual time=0.023..37.372 rows=49271 loops=1\) |
|               Index Cond: \(event\_time &gt;= \(now\(\) - '90 days'::interval\)\) |
|               Heap Fetches: 17088 |
|         -&gt;  Hash  \(cost=590.00..590.00 rows=13298 width=4\) \(actual time=7.828..7.830 rows=13298 loops=1\) |
|               Buckets: 16384  Batches: 1  Memory Usage: 596kB |
|               -&gt;  Seq Scan on customers c  \(cost=0.00..590.00 rows=13298 width=4\) \(actual time=0.025..5.400 rows=13298 loops=1\) |
|                     Filter: \(status = ANY \('{active,inactive}'::text\[\]\)\) |
|                     Rows Removed by Filter: 6702 |
| Planning Time: 0.458 ms |
| Execution Time: 70.277 ms |
