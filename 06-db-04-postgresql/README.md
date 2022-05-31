1.
```
\l - список БД
\c[onnect] {[DBNAME|- USER|- HOST|- PORT|-] | conninfo} connect to new database (currently "postgres") - подключение к БД
\dt[S+] [PATTERN] - список таблиц
\d[S+]  NAME - описание содержимого таблиц
\q - выход из psql
```
2.
```
test_database=# analyze verbose orders;
INFO:  analyzing "public.orders"
INFO:  "orders": scanned 1 of 1 pages, containing 8 live rows and 0 dead rows; 8 rows in sample, 8 estimated total rows
ANALYZE
```
```
test_database=# select avg_width from pg_stats where tablename='orders';
 avg_width
-----------
         4
        16
         4
(3 rows)
```
3.
Да, можно было избежать разбиения таблицы вручную, необходимо было определить тип на моменте проектирования и создания - partitioned table
```
test_database=# 
begin;
    create table orders_new (
        id integer NOT NULL,
        title varchar(80) NOT NULL,
        price integer) partition by range(price);
    create table orders_less partition of orders_new for values from (0) to (499);
    create table orders_more partition of orders_new for values from (499) to (99999);
    insert into orders_new (id, title, price) select * from orders;
commit;
BEGIN
CREATE TABLE
CREATE TABLE
CREATE TABLE
INSERT 0 8
COMMIT
```
4.
```
root@ubuntu-home:/# pg_dump -d test_database > /backup13/db_dump.sql
```
Для определения занчения столбца title можно было бы использовать индекс, для обеспечения уникальности.
