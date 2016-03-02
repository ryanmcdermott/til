# \pset null

Postgres natively shows NULL values show as spaces. Empty strings also are represented as a blank space, which can cause distinction issues.

```
db=# INSERT INTO places (city) VALUES ('');
INSERT 0 1
db=# INSERT INTO places (city) VALUES (NULL);
INSERT 0 1
db=# SELECT * FROM places;
 id |     name
----+---------------
  1 | Austin
  2 | San Francisco
  3 |
  4 |
(4 rows)
```

It's easy to contrast NULL values from empty strings by setting NULL values to a different value. You could even use emojis!

```
db=# \pset null '💩'
Null display is "💩".
db=# SELECT * FROM places;
 id |     name
----+---------------
  1 | Austin
  2 | San Francisco
  3 |
  4 | 💩
(4 rows)
```
