# Node Sequelize Poc

A POC using Node.js, Express.js, Sequelize.js and PostgreSQL.

## Start

## Setup

Create a user and db

```sh
psql postgres --u postgres
```

Create a new user (zeno) with password (paradox) then give access for creating the database.

```
postgres-# CREATE ROLE zeno WITH LOGIN PASSWORD 'paradox';
postgres-# ALTER ROLE zeno CREATEDB;
postgres-# exit
```

Now login with the created user.

```sh
psql postgres -U zeno
```

Create a new DB and give all privileges to it.

```
postgres=> CREATE DATABASE node_sequelize;
postgres=> GRANT ALL PRIVILEGES ON DATABASE node_sequelize TO zeno;
postgres=> exit
```

## Requiriments

sequelize-cli
PostgreSQL