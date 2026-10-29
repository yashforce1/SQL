<!-- If you're talking about SQL strings, like CITY, you can get the first or last character using ****LEFT() / RIGHT()** in MySQL. -->

// First letter
LEFT(CITY, 1)



// Last letter
RIGHT(CITY, 1)


Another common way

Using SUBSTRING():

SUBSTRING(CITY, 1, 1)                 -- first letter
SUBSTRING(CITY, LENGTH(CITY), 1)      -- last letter



<!-- THE index start with 1  -->
<!-- substring(column_name , position , count) -->



whats the differnece between union  and union all

UNION = COMBINE + REMOVE DUPLICATES
UNION ALL = COMBINE ALL ROWS.


