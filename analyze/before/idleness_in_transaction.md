| pid | state | duration | query |
| :--- | :--- | :--- | :--- |
| 32744 | active | 0 years 0 mons 0 days 0 hours 0 mins 23.509167 secs | <br/>        SET lock\_timeout = '20s';<br/>        UPDATE customers<br/>        SET phone = 'changed\_' \|\| NOW\(\)::TEXT<br/>        WHERE customer\_id = 1;<br/>         |
| 38040 | idle in transaction | 0 years 0 mons 0 days 0 hours 0 mins 23.046217 secs | <br/>                    UPDATE customers<br/>                    SET status = 'active'<br/>                    WHERE customer\_id = 1;<br/>                 |
| 28164 | active | 0 years 0 mons 0 days 0 hours 0 mins 8.848332 secs | <br/>        SET lock\_timeout = '20s';<br/>        UPDATE customers<br/>        SET phone = 'changed\_' \|\| NOW\(\)::TEXT<br/>        WHERE customer\_id = 1;<br/>         |
| 37988 | active | 0 years 0 mons 0 days 0 hours 0 mins 8.535792 secs | <br/>                    UPDATE customers<br/>                    SET country = country<br/>                    WHERE customer\_id = 1;<br/>                 |
| 544 | idle in transaction | 0 years 0 mons 0 days 0 hours 0 mins 8.15955 secs | <br/>                    UPDATE customers<br/>                    SET status = 'active'<br/>                    WHERE customer\_id = 5;<br/>                 |
| 30384 | active | 0 years 0 mons 0 days 0 hours 0 mins 0.0 secs | SELECT pid, state, now\(\) - xact\_start AS duration, query<br/>FROM pg\_stat\_activity<br/>WHERE xact\_start IS NOT NULL<br/>ORDER BY xact\_start |
