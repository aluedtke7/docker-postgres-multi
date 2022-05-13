# docker-postgres-multi


## Fork
This is a fork of https://github.com/lmm-git/docker-postgres-multi. The changes are:

- using latest PostgreSQL base image (currently v14)
- don't create additional user as SUPERUSER

## Description

Docker image to run a **PostgreSQL** database in a docker container with multiple users and databases.

Image is based of the official postgres:14 image. It modifies the `docker-entrypoint.sh` to allow setup of multiple users and databases. Therefore there are two new environment variables that can be set `POSTGRES_USERS` and `POSTGRES_DATABASES`. The functionality of `POSTGRES_USER` and `POSTGRES_DB` is unimpeded. If set the given user and database will be created in addition to the other given users.

### Usage

```sh
docker run -p 5432:5432 --name postgres-multi \
  -e POSTGRES_USER="postgres" \
  -e POSTGRES_PASSWORD="postgres" \
  -e POSTGRES_USERS="user1:password1|user2:password2|user3:password3" \
  -e POSTGRES_DATABASES="db1:user1|db2:user2|db3:user3" \
  -it --rm andreasluedtke/postgres-multi
```
