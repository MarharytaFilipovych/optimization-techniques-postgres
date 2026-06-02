| QUERY PLAN |
| :--- |
| Finalize Aggregate  \(cost=15733.44..15733.45 rows=1 width=8\) \(actual time=215.937..232.669 rows=1 loops=1\) |
|   -&gt;  Gather  \(cost=15733.33..15733.44 rows=1 width=8\) \(actual time=215.930..232.663 rows=2 loops=1\) |
|         Workers Planned: 1 |
|         Workers Launched: 1 |
|         -&gt;  Partial Aggregate  \(cost=14733.33..14733.34 rows=1 width=8\) \(actual time=177.467..178.832 rows=1 loops=2\) |
|               -&gt;  Parallel Hash Join  \(cost=11719.57..14415.46 rows=127150 width=0\) \(actual time=120.854..165.708 rows=98080 loops=2\) |
|                     Hash Cond: \(o.customer\_id = c.customer\_id\) |
|                     -&gt;  Parallel Seq Scan on orders o  \(cost=0.00..1934.46 rows=70646 width=4\) \(actual time=0.052..6.835 rows=60000 loops=2\) |
|                     -&gt;  Parallel Hash  \(cost=11539.09..11539.09 rows=14439 width=8\) \(actual time=119.850..121.212 rows=16368 loops=2\) |
|                           Buckets: 65536  Batches: 1  Memory Usage: 1824kB |
|                           -&gt;  Hash Join  \(cost=766.55..11539.09 rows=14439 width=8\) \(actual time=7.303..102.207 rows=16368 loops=2\) |
|                                 Hash Cond: \(e.customer\_id = c.customer\_id\) |
|                                 -&gt;  Parallel Seq Scan on customer\_events\_wide e  \(cost=0.00..10715.51 rows=21719 width=4\) \(actual time=0.013..85.246 rows=24638 loops=2\) |
|                                       Filter: \(event\_time &gt;= \(now\(\) - '90 days'::interval\)\) |
|                                       Rows Removed by Filter: 75362 |
|                                 -&gt;  Hash  \(cost=595.81..595.81 rows=13659 width=4\) \(actual time=7.188..7.189 rows=13298 loops=2\) |
|                                       Buckets: 16384  Batches: 1  Memory Usage: 596kB |
|                                       -&gt;  Seq Scan on customers c  \(cost=0.00..595.81 rows=13659 width=4\) \(actual time=0.253..4.990 rows=13298 loops=2\) |
|                                             Filter: \(status = ANY \('{active,inactive}'::text\[\]\)\) |
|                                             Rows Removed by Filter: 6702 |
| Planning Time: 0.764 ms |
| Execution Time: 232.809 ms |
