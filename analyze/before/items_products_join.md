| QUERY PLAN |
| :--- |
| Sort  \(cost=8679.49..8679.51 rows=5 width=47\) \(actual time=217.224..223.843 rows=5 loops=1\) |
|   Sort Key: \(sum\(\(\(oi.quantity\)::numeric \* oi.unit\_price\)\)\) DESC |
|   Sort Method: quicksort  Memory: 25kB |
|   -&gt;  Finalize GroupAggregate  \(cost=8678.75..8679.44 rows=5 width=47\) \(actual time=217.206..223.835 rows=5 loops=1\) |
|         Group Key: p.category |
|         -&gt;  Gather Merge  \(cost=8678.75..8679.32 rows=5 width=47\) \(actual time=217.195..223.816 rows=10 loops=1\) |
|               Workers Planned: 1 |
|               Workers Launched: 1 |
|               -&gt;  Sort  \(cost=7678.74..7678.75 rows=5 width=47\) \(actual time=183.042..183.044 rows=5 loops=2\) |
|                     Sort Key: p.category |
|                     Sort Method: quicksort  Memory: 25kB |
|                     Worker 0:  Sort Method: quicksort  Memory: 25kB |
|                     -&gt;  Partial HashAggregate  \(cost=7678.62..7678.68 rows=5 width=47\) \(actual time=182.994..182.998 rows=5 loops=2\) |
|                           Group Key: p.category |
|                           Batches: 1  Memory Usage: 24kB |
|                           Worker 0:  Batches: 1  Memory Usage: 24kB |
|                           -&gt;  Hash Join  \(cost=66.00..5032.63 rows=211679 width=17\) \(actual time=1.020..76.336 rows=179928 loops=2\) |
|                                 Hash Cond: \(oi.product\_id = p.product\_id\) |
|                                 -&gt;  Parallel Seq Scan on order\_items oi  \(cost=0.00..4409.79 rows=211679 width=14\) \(actual time=0.005..17.509 rows=179928 loops=2\) |
|                                 -&gt;  Hash  \(cost=41.00..41.00 rows=2000 width=11\) \(actual time=0.984..0.985 rows=2000 loops=2\) |
|                                       Buckets: 2048  Batches: 1  Memory Usage: 104kB |
|                                       -&gt;  Seq Scan on products p  \(cost=0.00..41.00 rows=2000 width=11\) \(actual time=0.359..0.622 rows=2000 loops=2\) |
| Planning Time: 3.561 ms |
| Execution Time: 224.022 ms |
