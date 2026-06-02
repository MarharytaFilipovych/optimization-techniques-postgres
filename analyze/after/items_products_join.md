| QUERY PLAN |
| :--- |
| Sort  \(cost=8432.18..8432.19 rows=5 width=71\) \(actual time=105.285..105.430 rows=5 loops=1\) |
|   Sort Key: \(sum\(\(sum\(\(\(order\_items.quantity\)::numeric \* order\_items.unit\_price\)\)\)\)\) DESC |
|   Sort Method: quicksort  Memory: 25kB |
|   -&gt;  HashAggregate  \(cost=8432.04..8432.12 rows=5 width=71\) \(actual time=105.237..105.385 rows=5 loops=1\) |
|         Group Key: p.category |
|         Batches: 1  Memory Usage: 24kB |
|         -&gt;  Hash Join  \(cost=8366.78..8417.04 rows=2000 width=47\) \(actual time=102.230..104.334 rows=2000 loops=1\) |
|               Hash Cond: \(order\_items.product\_id = p.product\_id\) |
|               -&gt;  Finalize HashAggregate  \(cost=8300.78..8325.78 rows=2000 width=44\) \(actual time=101.769..103.123 rows=2000 loops=1\) |
|                     Group Key: order\_items.product\_id |
|                     Batches: 1  Memory Usage: 1393kB |
|                     -&gt;  Gather  \(cost=8055.78..8280.78 rows=2000 width=44\) \(actual time=94.689..97.019 rows=4000 loops=1\) |
|                           Workers Planned: 1 |
|                           Workers Launched: 1 |
|                           -&gt;  Partial HashAggregate  \(cost=7055.78..7080.78 rows=2000 width=44\) \(actual time=78.933..79.945 rows=2000 loops=2\) |
|                                 Group Key: order\_items.product\_id |
|                                 Batches: 1  Memory Usage: 1137kB |
|                                 Worker 0:  Batches: 1  Memory Usage: 1137kB |
|                                 -&gt;  Parallel Seq Scan on order\_items  \(cost=0.00..4409.79 rows=211679 width=14\) \(actual time=0.004..10.933 rows=179928 loops=2\) |
|               -&gt;  Hash  \(cost=41.00..41.00 rows=2000 width=11\) \(actual time=0.443..0.444 rows=2000 loops=1\) |
|                     Buckets: 2048  Batches: 1  Memory Usage: 104kB |
|                     -&gt;  Seq Scan on products p  \(cost=0.00..41.00 rows=2000 width=11\) \(actual time=0.044..0.178 rows=2000 loops=1\) |
| Planning Time: 0.484 ms |
| Execution Time: 106.939 ms |
