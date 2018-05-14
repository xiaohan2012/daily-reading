# learned

for `pyspark.sql`

- `df.groupy(df.field).{agg|count|mean...}`
- `agg(collect_list(struct('field name)))` to gather a list
  - can be used to build inverted index
  - `struct('field name')` to extract id
- `df.rdd` to get the RDD, which has methods like `flatMap`, `map`
- `RDD.flatMap` first `map` then `flatten`, `map` just does the map
- `df.drop_duplicates` to drop duplicates

`join` example


```
    df_cosine = (
        df_user_pairs
            .alias('m')   # !!
            .join(df_user_ratings.alias("u"), col("u.user_id") == col("m.user_1"))  # col !!
            .join(df_user_ratings.alias("v"), col("v.user_id") == col("m.user_2"))
            .select(
                col('m.user_1').alias('user_1'),
                col('m.user_2').alias('user_2'),
                cos_udf('u.ratings', 'v.ratings').alias('cosine_similarity')  # use of user defined function
            )
    )
```

- `StructType` used to define a DataFrame schema


example of `partitionBy` and `rank`: find top-k for each group/partition

- `withColumn` to add column

```
top_user =  df_cosine_dual.withColumn(
  "rank", dense_rank().over(Window.partitionBy("user_1").orderBy(desc("cosine_similarity"))))
top_user = top_user.filter(top_user["rank"] <= K)
```

or can be done via `groupBy(...).agg(...)`, where a function that extracts the top-k is passed to `agg`





