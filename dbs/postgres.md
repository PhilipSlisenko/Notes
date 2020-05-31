### UPSERT (Insert or if exists Update)
 Instead of common workflow of first checking if exists and then iserting or updating accordingly.  
```SQL
INSERT INTO table_name(column_list) VALUES(value_list)
ON CONFLICT target action; 
```
### CASE
During SELECT you can use CASE you can create new columns based on some predicate.
```SQL
CASE 
      WHEN condition_1  THEN result_1
      WHEN condition_2  THEN result_2
      [WHEN ...]
      [ELSE result_n]
END
```
```sql
SELECT name,
       (CASE WHEN population<1000000 
            THEN 'small'
            WHEN population<10000000 
            THEN 'medium'
            ELSE 'large'
       END) as population
  FROM bbc
```