<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

This is an inline math formula: \( E = mc^2 \).

This is a block math formula:
$$ E = mc^2 $$

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


