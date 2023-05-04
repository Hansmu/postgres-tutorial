# Union and intersection

You can use the `UNION` keyword to combine the results of multiple `SELECT` statements.

So let's look at an example, where we want to find the 4 products with the highest price and the 4 products with the highest price/weight ratio.

```sql
(
    SELECT *
      FROM products
     ORDER
        BY price DESC
     LIMIT 4
)
UNION
(
    SELECT *
      FROM products
     ORDER
        BY price / weight DESC
     LIMIT 4
);
```
If the `UNION` keyword sees identical rows, it will remove the duplicates.
If we want to keep the duplicates, we can use the `UNION ALL` keyword.

```sql
(
    SELECT *
      FROM products
     ORDER
        BY price DESC
     LIMIT 4
)
UNION ALL
(
    SELECT *
      FROM products
     ORDER
        BY price / weight DESC
     LIMIT 4
);
```

You can only use the `UNION` keyword when the result sets have the same columns.
That is, they have the same names AND the same types.

# Intersection

You can use the `INTERSECT` keyword to find the rows that are in both result sets.
Similar to `UNION`, you can add the `ALL` keyword to keep duplicates.
By default, duplicates are removed.

A duplicate in this context means that there's more than one of the same row inside one of the sub-sets.
If both subsets have only a single item, then that does not indicate a duplicate.

```sql
(
    SELECT *
      FROM products
     ORDER
        BY price DESC
     LIMIT 4
)
INTERSECT
(
    SELECT *
      FROM products
     ORDER
        BY price / weight DESC
     LIMIT 4
);
```

# Difference

You can use the `EXCEPT` keyword to find the rows that are in the first result set but not in the second result set.
Again, it removes duplicates.
If you want to keep duplicates, you can use the `EXCEPT ALL` keyword.

Remember, the set that you get depends on the order of the sub-sets in your statement.

```sql
(
    SELECT *
      FROM products
     ORDER
        BY price DESC
     LIMIT 4
)
EXCEPT
(
    SELECT *
      FROM products
     ORDER
        BY price / weight DESC
     LIMIT 4
);
```