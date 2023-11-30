#SQL

###nested sql
with this you can get a data from another table in a commond sql
```sql
SELECT * , (SELECT `name` FROM `categories` WHERE `categories`.`cat_id`) AS `category` FROM `articles` WHERE id = ?;
```