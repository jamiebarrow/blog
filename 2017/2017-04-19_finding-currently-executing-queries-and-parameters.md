# 2017-04-19 Finding currently executing queries and parameters

tags: executing queries, mssql, parameterized sql, query plan, sql

If you've worked with an Object Relational Mapper (ORM) such as [Hibernate](https://hibernate.org/), [NHibernate](https://nhibernate.info/), [Entity Framework](https://docs.microsoft.com/en-us/ef/), etc., then you'll know these sometimes convert your queries into parameterized queries that can become quite beastly.

Trying to debug it means either profiling the database to see what queries are executing, and then seeing the query and values from there, or if you can't profile it, maybe selecting from some system tables to do a similar thing.

This snippet below ([thanks again StackOverflow](https://stackoverflow.com/a/2509831/222090)) will give you some nice details about the queries on a database, including an XML query plan that contains the parameters that were used when generating the query plan. It can be useful in diagnosing slow queries:


```sql
select * 
from sys.dm_exec_requests r 
cross apply sys.dm_exec_query_plan(plan_handle) as qp
cross apply sys.dm_exec_sql_text(r.sql_handle) 
where r.database_id = DB_ID('<dbname>')
```
