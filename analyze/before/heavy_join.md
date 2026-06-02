| QUERY PLAN |
| :--- |
| Limit  \(cost=4073.47..4073.72 rows=100 width=58\) \(actual time=86.720..86.750 rows=100 loops=1\) |
|   -&gt;  Sort  \(cost=4073.47..4090.65 rows=6873 width=58\) \(actual time=86.717..86.732 rows=100 loops=1\) |
|         Sort Key: \(sum\(o.total\_amount\)\) DESC |
|         Sort Method: top-N heapsort  Memory: 38kB |
|         -&gt;  HashAggregate  \(cost=3724.87..3810.78 rows=6873 width=58\) \(actual time=78.153..83.205 rows=6672 loops=1\) |
|               Group Key: c.customer\_id |
|               Batches: 1  Memory Usage: 3281kB |
|               -&gt;  Hash Join  \(cost=681.73..3423.79 rows=40144 width=28\) \(actual time=5.411..52.345 rows=39879 loops=1\) |
|                     Hash Cond: \(o.customer\_id = c.customer\_id\) |
|                     -&gt;  Seq Scan on orders o  \(cost=0.00..2427.00 rows=120000 width=14\) \(actual time=0.015..13.665 rows=120000 loops=1\) |
|                     -&gt;  Hash  \(cost=595.81..595.81 rows=6873 width=18\) \(actual time=5.372..5.373 rows=6693 loops=1\) |
|                           Buckets: 8192  Batches: 1  Memory Usage: 393kB |
|                           -&gt;  Seq Scan on customers c  \(cost=0.00..595.81 rows=6873 width=18\) \(actual time=0.012..4.033 rows=6693 loops=1\) |
|                                 Filter: \(status = 'active'::text\) |
|                                 Rows Removed by Filter: 13307 |
| Planning Time: 0.968 ms |
| Execution Time: 87.555 ms |
