# MySQL on Hasura

- Create a secret to hold root password:
  ```bash
  $ hasura secrets update mysql.password <secure-password>
  # you can verify it is set using 
  $ hasura secrets list
  ```
This password will be taken in by MySQL as `MYSQL_ROOT_PASSWORD`

### Connection parameters:

- username: `root`
- password: value set as `MYSQL_ROOT_PASSWORD`
- hostname: `mysql.default` (check by executing `$ hasura microservice list`)
- port: `3306`
