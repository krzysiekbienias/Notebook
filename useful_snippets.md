# Regular expresions
How to find records that starts and and end with letter a.

```sql
where city regexp '^A.*a$'
```

* ^a: The string starts with a.
* .* Any sequence of characters (zero or more).
* a$ the string ends with a

Remember that REGEXP in MySQL are cse-insensitive so we don't need to explicity match both uppercase and lowercase vowels.


# HackerRank
Contest leaderboard use cte
