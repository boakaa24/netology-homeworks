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
