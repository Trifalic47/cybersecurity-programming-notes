***

Use  `sudo mysql` to get into the mysql shell.Now list the databases using `show databases;`
then make an database using `create database <name>` and then use it using `use <name>`
.Now make an new  table using :
```sql
create table coffeeTable(
	id int,
	name varchar(255),
	region varchar(255),
	roast varchar(255)
); 
```

Now its time to add the rows into the table those upper things were column
do:
```sql
insert into coffeeTable values (1,"hacker","earth","light");
```

Now to show the data you can do:
```sql
select * from coffeeTable;
```

It would look like this

![[Pasted image 20260204234302.png]]


Select needed things like:
```sql
select * from coffeeTable where rost = "medium"
```

```sql
select alias from user where age > 30;
select alias from user where origin = "earth" or origin = "asgard";
select * from user where not origin = "earth";
delete from user where first_name = "jeff";
delete from user where first_name = "jeff" and age = 49;
update user set id = 2 where first_name = "newbie";
select * from user order by age asc;
select * from user order by age desc;
alter table user add beard boolean;
ALTER table user RENAME TO users;
SELECT COUNT(*) AS ADMIN FROM users WHERE role "admin";
SELECT * FROM users LIMIT 2 OFFSET 3;
SELECT * FROM users ORDER BY networth DESC LIMIT 1;
SELECT DISTINCT role FROM users;
SELECT * FROM users WHERE first_name LIKE 'El%';
let q = "SELECT * FROM users WHERE first_name LIKE '%" + input + "%'";
```
