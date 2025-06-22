Main Flow:- 
-Read the raw products_day1.csv and products_day2.csv  as Pandas DataFrames. 

-Load into in-memory SQL tables day1, day2 using to_sql() for structured querying. 

-Use SQL joins to detect full-row additions and removals  by comparing key values

-Perform column-level comparison to find field-specific changes between matched keys. 

-Concatenate and export full-row diffs and column diffs as separate CSVs.

-print the full-row diffs and column diff sorted by product_id to the screen.


Functions used:-

-load_csv_to_db() Reads a CSV into a DataFrame and loads it as a SQL table.

-compare_tables() Detects REMOVED and ADDED rows via LEFT OUTER JOIN and IS NULL and Detects column-level diffs using inner 
join and != or null and returns two data frames one for row changes and other for column changes

-compare_snapshots() Setups SQLite engine, Load both CSVs to tables and Call compare_tables() and return results


sql code used:-
-for finding removed and added rows
    SELECT day1.*,'REMOVED' AS change_type
    FROM day1 LEFT JOIN day2 
    ON day1.product_id = day2.product_id
    WHERE day2.product_id IS NULL;
    UNION ALL
    SELECT day2.*,'ADDED' AS change_type
    FROM day2 LEFT JOIN day1 
    ON day2.product_id = day1.product_id
    WHERE day1.product_id IS NULL;

-for findng the value difference
    SELECT day1.product_id,'price' AS column_changed,day1.price AS old_value,day2.price AS new_value
    FROM day1 JOIN day2 ON day1.product_id = day2.product_id
    WHERE (day1.price IS NOT day2.price OR
     day1.price IS NULL AND day2.price IS NOT NULL OR
     day1.price IS NOT NULL AND day2.price IS NULL);

