1.
```
version: "3.9"

volumes:
  postgressql_data:  
  backup_postgressql_data:

services:
  postgressql:
    image: postgres:14.3-bullseye
    container_name: postgressql
    environment:
      - PGDATA=/var/lib/postgresql/data/
      - POSTGRES_USER:"postgres"
      - POSTGRES_PASSWORD=12345
    volumes:
      - postgressql_data:/var/lib/postgresql/data
      - backup_postgressql_data:/backup
      - ./config:/docker-entrypoint-initdb.d
    network_mode: "host"
```
2.
```
test_db=# \list
                                 List of databases
   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileg
es
-----------+----------+----------+------------+------------+------------------
-----
 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 |
 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres
    +
           |          |          |            |            | postgres=CTc/post
gres
 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres
    +
           |          |          |            |            | postgres=CTc/post
gres
 test_db   | postgres | UTF8     | en_US.utf8 | en_US.utf8 |
(4 rows)
```
```
test_db=# \d+ orders
                                                                Table "public.orders"
   Column   |         Type          | Collation | Nullable |              Default               | Storage  | Compre
ssion | Stats target | Description
------------+-----------------------+-----------+----------+------------------------------------+----------+-------
------+--------------+-------------
 id         | integer               |           | not null | nextval('orders_id_seq'::regclass) | plain    |
      |              |
 order_name | character varying(25) |           | not null |                                    | extended |
      |              |
 price      | integer               |           | not null |                                    | plain    |
      |              |
Indexes:
    "orders_pkey" PRIMARY KEY, btree (id)
Check constraints:
    "orders_order_name_check" CHECK (order_name::text <> ''::text)
    "orders_price_check" CHECK (price > 0)
Referenced by:
    TABLE "clients" CONSTRAINT "clients_order_number_fkey" FOREIGN KEY (order_number) REFERENCES orders(id)
Access method: heap
```
```
test_db=# \d+ clients
                                                                 Table "public.clients"
    Column    |         Type          | Collation | Nullable |               Default               | Storage  | Com
pression | Stats target | Description
--------------+-----------------------+-----------+----------+-------------------------------------+----------+----
---------+--------------+-------------
 id           | integer               |           | not null | nextval('clients_id_seq'::regclass) | plain    |
         |              |
 last_name    | character varying(45) |           | not null |                                     | extended |
         |              |
 country      | character varying(35) |           | not null |                                     | extended |
         |              |
 order_number | integer               |           |          |                                     | plain    |
         |              |
Indexes:
    "clients_pkey" PRIMARY KEY, btree (id)
Check constraints:
    "clients_country_check" CHECK (country::text <> ''::text)
    "clients_last_name_check" CHECK (last_name::text <> ''::text)
Foreign-key constraints:
    "clients_order_number_fkey" FOREIGN KEY (order_number) REFERENCES orders(id)
Access method: heap
```
```
SELECT table_name, grantee, privilege_type 
	FROM information_schema.role_table_grants 
	WHERE table_name='orders'
  
SELECT table_name, grantee, privilege_type 
	FROM information_schema.role_table_grants 
	WHERE table_name='clients'
  ```
  ```
"orders"	"postgres"	        "INSERT"
"orders"	"postgres"	        "SELECT"
"orders"	"postgres"	        "UPDATE"
"orders"	"postgres"	        "DELETE"
"orders"	"postgres"	        "TRUNCATE"
"orders"	"postgres"	        "REFERENCES"
"orders"	"postgres"	        "TRIGGER"
"orders"	"test-simple-user"	"INSERT"
"orders"	"test-simple-user"	"SELECT"
"orders"	"test-simple-user"	"UPDATE"
"orders"	"test-simple-user"	"DELETE"
```
```
"clients"	"postgres"	        "INSERT"
"clients"	"postgres"	        "SELECT"
"clients"	"postgres"	        "UPDATE"
"clients"	"postgres"	        "DELETE"
"clients"	"postgres"	        "TRUNCATE"
"clients"	"postgres"	        "REFERENCES"
"clients"	"postgres"	        "TRIGGER"
"clients"	"test-simple-user"	"INSERT"
"clients"	"test-simple-user"	"SELECT"
"clients"	"test-simple-user"	"UPDATE"
"clients"	"test-simple-user"	"DELETE"
```
3.
```
SELECT COUNT(*) FROM orders

"count"
5

SELECT COUNT(*) FROM clients

"count"
5
```
4.
```
UPDATE clients SET order_number=3 WHERE id=1;
UPDATE clients SET order_number=4 WHERE id=2;
UPDATE clients SET order_number=5 WHERE id=3
```
```
SELECT * FROM clients WHERE order_number IS NOT NULL

"id"	"last_name"		"country"	"order_number"
1	"???????????? ???????? ????????????????"	"USA"		3
2	"???????????? ???????? ????????????????"	"Canada"	4
3	"???????????? ?????????????????? ??????"	"Japan"		5
```
5.
```
- Plan: 
    Node Type: ""Seq Scan""
    Parallel Aware: false
    Async Capable: false
    Relation Name: ""clients""
    Alias: ""clients""
    Startup Cost: 0.00
    Total Cost: 13.50
    Plan Rows: 348
    Plan Width: 204
    Filter: ""(order_number IS NOT NULL)
    
    EXPLAIN - ?????????????????? ?????? ???????? ?????????????????? ???????????????????? ?? ?????????????? ?? ????, ?? ?????? ?????????? ?????????? ???? ???????????????????? ??????????????,
    ?????? ?????? ?????????????????????? ???????????? ???? ???????????????? ?????????? ???????????????? ??????????????????????.  
  ```
6.
```
root@ubuntu-home:~/docker-compose-PostgreSQL# docker exec -it postgressql bash
root@ubuntu-home:/# pg_dumpall > /backup/backup_"`date +"%d-%m-%Y"`"
root@ubuntu-home:/# ls backup
backup_24-05-2022
root@ubuntu-home:~/docker-compose-PostgreSQL# docker-compose down
Stopping postgressql ... done
Removing postgressql ... done
root@ubuntu-home:~/docker-compose-PostgreSQL# docker volume ls
DRIVER    VOLUME NAME
local     docker-compose-postgresql_backup_postgressql_data
local     docker-compose-postgresql_postgressql_data
root@ubuntu-home:~/docker-compose-PostgreSQL# docker volume rm docker-compose-postgresql_postgressql_data
docker-compose-postgresql_postgressql_data
root@ubuntu-home:~/docker-compose-PostgreSQL# docker volume ls
DRIVER    VOLUME NAME
local     docker-compose-postgresql_backup_postgressql_data
root@ubuntu-home:~/docker-compose-PostgreSQL# docker-compose up -d
Starting postgressql ... done
root@ubuntu-home:~/docker-compose-PostgreSQL# docker exec -it postgressql bash
root@ubuntu-home:/# psql -f /backup/backup_24-05-2022

test_db=# \l
                                 List of databases
   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges
-----------+----------+----------+------------+------------+-----------------------
 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 |
 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
 test_db   | postgres | UTF8     | en_US.utf8 | en_US.utf8 |
(4 rows)
```
