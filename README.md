# Node Sequelize Poc

A POC using Node.js, Express.js, Sequelize.js and PostgreSQL.

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

Install npm modules and start

```sh
cd node-sequelize-poc && npm i && npm run dev
```

test CURLs:

```sh
curl -i -X POST -H "Content-Type: application/json" -d '{ "class_name":"Class A","students": [{ "student_name":"John Doe" },{ "student_name":"Jane Doe" },{ "student_name":"Doe Doel" }] }' localhost:3000/api/classroom/add_with_students

curl -i -H "Accept: application/json" localhost:3000/api/classroom/2

curl -i -X POST -H "Content-Type: application/json" -d '{ "lecturer_name":"Kylian Mbappe","course": { "course_name":"English Grammar" }}' localhost:3000/api/lecturer/add_with_course

curl -i -X POST -H "Content-Type: application/json" -d '{ "student_id":1,"course_id": 1}' localhost:3000/api/student/add_course
```

Check data persist

`psql postgres -U zeno`

```
postgres=> \c node_sequelize

...

SELECT * FROM public."Students" WHERE classroom_id=2;
```

## Requiriments

sequelize-cli  
PostgreSQL