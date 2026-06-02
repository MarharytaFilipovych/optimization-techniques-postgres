| QUERY PLAN |
| :--- |
| Seq Scan on customers  \(cost=0.00..594.06 rows=2 width=96\) \(actual time=4.197..4.198 rows=0 loops=1\) |
|   Filter: \(email \~\~ '%gmail%'::text\) |
|   Rows Removed by Filter: 20000 |
| Planning Time: 1.545 ms |
| Execution Time: 4.215 ms |
