# about this repo
this repo is used to migrate the db by flyway when use the vault store the db username and password

# docker image
[docker hub](https://hub.docker.com/r/tianyawy/flyway-vault/)

# docker-compose

```
version: '2.1'
services:
  migration:
    image: tianyawy/flyway-vault:1.0
    container_name: migrtor-db
    command: migrate
    environment:
      - VAULT_TOKEN=${VAULT_TOKEN}
      - VAULT_CONNECT=${DBIP}:8201
      - VAULT_DB_PATH=secret
      - VAULT_DB_ROLE=migrator
      - DB_URL=jdbc:postgresql://${DBIP}:5436/your-db-name
    volumes:
      - ./test/migrate:/flyway/sql
```


