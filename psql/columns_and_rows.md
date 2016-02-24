# Display Columns as Rows in Postgres

`\x` turns the Postgres CLI from column view to row view:

```
database=# select * from users limit 1;
id  |     name     |      date_created      
-----+--------------+------------------------
85 | John Smith | 2015-08-10 08:57:14+00
(1 row)

database=# \x
Expanded display is on.

database=# select * from users limit 1;
-[ RECORD 1 ]+-----------------------
id           | 85
name         | John Smith
date_created | 2015-08-10 08:57:14+00
```