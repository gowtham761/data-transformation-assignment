Main Flow:-

-Read the raw CSV as text without interpreting quotes.

-Fix records to remove extra quote marks.

-Clean the data using clean_dataframe.

-Write the cleaned CSV as cleaned_sales.csv.

Print the cleaned DataFrame to the screen.


Functions used:-

-strip_all_quotes() Cleans  string by removing HTML entities like &quot , double quotes, and spaces.

-to_int() Cleans and converts a value to integer and returns 0 if invalid.

-to_float() Cleans and converts to float and returns 0.0 if invalid.

-to_datetime() Cleans and formats date into YYYY-MM-DD format and returns "" if invalid.

-compute_total_price() Multiplies quantity and price to calculate total.

-clean_dataframe() Applies the above functions to fix the entire DataFrame and add total_price.