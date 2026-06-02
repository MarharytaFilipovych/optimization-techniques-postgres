| QUERY PLAN |
| :--- |
| Bitmap Heap Scan on customers  \(cost=32.02..39.58 rows=2 width=96\) \(actual time=0.038..0.039 rows=0 loops=1\) |
|   Recheck Cond: \(email \~\~ '%gmail%'::text\) |
|   -&gt;  Bitmap Index Scan on index\_customers\_email  \(cost=0.00..32.01 rows=2 width=0\) \(actual time=0.036..0.036 rows=0 loops=1\) |
|         Index Cond: \(email \~\~ '%gmail%'::text\) |
| Planning Time: 1.308 ms |
| Execution Time: 0.092 ms |
