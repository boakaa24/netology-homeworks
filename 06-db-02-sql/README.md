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
