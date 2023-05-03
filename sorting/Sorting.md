# Sorting

In order to sort data, you can use the `ORDER BY` keyword.

The default order is ascending, but you can specify descending order by using the `DESC` keyword.

```sql
SELECT *
  FROM photos
 ORDER
    BY likes DESC;
```

You can also sort by multiple columns.

```sql
SELECT *
  FROM products
 ORDER
    BY price DESC,
       weight;
```

## Pagination

You can use the `LIMIT` keyword to limit the number of rows that are returned.

```sql
SELECT *
  FROM photos
 LIMIT 10;
```

You can also use the `OFFSET` keyword to skip a certain number of rows.
For example, if you'd want to skip the first item, then you'd say `OFFSET 1`.
Remember, this is zero-indexed. 
Also, keep in mind that you're skipping rows with the `OFFSET` keyword, not pages. 
So when you're paginating, you'll need to multiply the page number by the number of items per page.

```sql
SELECT *
  FROM photos
 LIMIT 10
OFFSET 10;
```

So pagination is a combination of using `LIMIT` and `OFFSET`.
You use `LIMIT` to specify the number of items per page and `OFFSET` to specify the page number.


