| QUERY PLAN |
| :--- |
| Limit  \(cost=6056.55..6057.05 rows=200 width=27\) \(actual time=126.005..126.047 rows=200 loops=1\) |
|   -&gt;  Sort  \(cost=6056.55..6106.49 rows=19977 width=27\) \(actual time=126.002..126.020 rows=200 loops=1\) |
|         Sort Key: \(count\(\*\)\) DESC |
|         Sort Method: top-N heapsort  Memory: 48kB |
|         -&gt;  HashAggregate  \(cost=4993.38..5193.15 rows=19977 width=27\) \(actual time=71.579..107.354 rows=62522 loops=1\) |
|               Group Key: customer\_id, event\_type |
|               Batches: 5  Memory Usage: 8241kB  Disk Usage: 688kB |
|               -&gt;  Index Only Scan using index\_customer\_events\_wide\_time\_customer\_type on customer\_events\_wide  \(cost=0.42..4011.21 rows=98217 width=19\) \(actual time=0.025..23.318 rows=98243 loops=1\) |
|                     Index Cond: \(event\_time &gt;= \(now\(\) - '180 days'::interval\)\) |
|                     Heap Fetches: 9148 |
| Planning Time: 0.135 ms |
| Execution Time: 148.150 ms |
