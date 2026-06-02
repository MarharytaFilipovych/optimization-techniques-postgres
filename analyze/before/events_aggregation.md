| QUERY PLAN |
| :--- |
| Limit  \(cost=14954.25..14954.75 rows=200 width=27\) \(actual time=373.302..373.339 rows=200 loops=1\) |
|   -&gt;  Sort  \(cost=14954.25..15006.12 rows=20746 width=27\) \(actual time=373.299..373.316 rows=200 loops=1\) |
|         Sort Key: \(count\(\*\)\) DESC |
|         Sort Method: top-N heapsort  Memory: 48kB |
|         -&gt;  HashAggregate  \(cost=13850.17..14057.63 rows=20746 width=27\) \(actual time=291.903..353.648 rows=62594 loops=1\) |
|               Group Key: customer\_id, event\_type |
|               Batches: 5  Memory Usage: 8241kB  Disk Usage: 696kB |
|               -&gt;  Seq Scan on customer\_events\_wide  \(cost=0.00..12820.49 rows=102968 width=19\) \(actual time=0.029..191.882 rows=98430 loops=1\) |
|                     Filter: \(event\_time &gt;= \(now\(\) - '180 days'::interval\)\) |
|                     Rows Removed by Filter: 101570 |
| Planning Time: 2.808 ms |
| Execution Time: 387.709 ms |
