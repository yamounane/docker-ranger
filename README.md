# Docker images for Apache Ranger Admin UI

## Build the docker images as follows:

```
 $ docker build -t yamounane/ranger-postgresql -f ~/docker-ranger/Dockerfile-postgres ~/docker-ranger/
 $ docker build -t yamounane/ranger-admin -f ~/docker-ranger/Dockerfile-ranger-admin ~/docker-ranger/
 $ docker-compose up
```

NB: The ranger-admin docker image takes a long time because it builds
the source code using Apache Maven.

## Manual build :

 * Create a network to link containers: 

```
$ docker network create ranger-network
```

 * Then, run with: 

```
$ docker run -p 5432:5432 --name postgres-server --network ranger-network yamounane/ranger-postgresql
$ docker run -p 6080:6080 -it --network ranger-network yamounane/ranger-admin
```

## Access 

 * http://localhost:6080 (admin/admin)
