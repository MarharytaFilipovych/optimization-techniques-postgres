| QUERY PLAN |
| :--- |
| Limit  \(cost=3991.52..3991.77 rows=100 width=58\) \(actual time=39.204..39.232 rows=100 loops=1\) |
|   -&gt;  Sort  \(cost=3991.52..4008.25 rows=6693 width=58\) \(actual time=39.200..39.215 rows=100 loops=1\) |
|         Sort Key: \(sum\(o.total\_amount\)\) DESC |
|         Sort Method: top-N heapsort  Memory: 38kB |
|         -&gt;  HashAggregate  \(cost=3652.06..3735.72 rows=6693 width=58\) \(actual time=31.014..35.997 rows=6672 loops=1\) |
|               Group Key: c.customer\_id |
|               Batches: 1  Memory Usage: 3281kB |
|               -&gt;  Hash Join  \(cost=587.48..3349.16 rows=40386 width=28\) \(actual time=1.909..20.270 rows=39879 loops=1\) |
|                     Hash Cond: \(o.customer\_id = c.customer\_id\) |
|                     -&gt;  Seq Scan on orders o  \(cost=0.00..2444.82 rows=120682 width=14\) \(actual time=0.011..7.069 rows=120000 loops=1\) |
|                     -&gt;  Hash  \(cost=503.82..503.82 rows=6693 width=18\) \(actual time=1.872..1.874 rows=6693 loops=1\) |
|                           Buckets: 8192  Batches: 1  Memory Usage: 393kB |
|                           -&gt;  Bitmap Heap Scan on customers c  \(cost=80.16..503.82 rows=6693 width=18\) \(actual time=0.179..1.236 rows=6693 loops=1\) |
|                                 Recheck Cond: \(status = 'active'::text\) |
|                                 Heap Blocks: exact=340 |
|                                 -&gt;  Bitmap Index Scan on index\_customers\_status  \(cost=0.00..78.48 rows=6693 width=0\) \(actual time=0.152..0.152 rows=6871 loops=1\) |
|                                       Index Cond: \(status = 'active'::text\) |
| Planning Time: 13.525 ms |
| Execution Time: 40.361 ms |
