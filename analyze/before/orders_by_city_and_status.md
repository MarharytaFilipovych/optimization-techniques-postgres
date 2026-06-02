| QUERY PLAN |
| :--- |
| Seq Scan on orders  \(cost=0.00..3027.00 rows=16324 width=50\) \(actual time=0.015..26.404 rows=16930 loops=1\) |
|   Filter: \(\(delivery\_city \~\~ '%a%'::text\) AND \(status = 'paid'::text\)\) |
|   Rows Removed by Filter: 103070 |
| Planning Time: 1.810 ms |
| Execution Time: 26.975 ms |
