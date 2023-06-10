# trial-mongodb

A [MongoDB](https://www.mongodb.com/docs/) bootstraper, using [mongo-express](https://github.com/mongo-express/mongo-express) as dashboard UI, and [official Node.js client driver](https://www.mongodb.com/docs/drivers/node/current/quick-start/)。

For desktop GUI, consider [MongoDB Compass](https://www.mongodb.com/products/compass)

## Service URL

- Database (MongoDB) [http://localhost:27017](http://localhost:27017)
- Web UI (mongo-express) [http://localhost:8081](http://localhost:8081)

## Default user for dashboard

None, as default.

## Usage

### Start a service group

Manage service stack with [Docker Compose](https://docs.docker.com/compose/), through NPM (optional).

```shell
# Start services
npm run docker:up

# Stop services and prune Docker volumes
npm run docker:down
```

### Start services individually

Launch database first, then the UI.

#### MySQL

```shell
docker run -p 27017:27017 -d --restart always --name=mongo mongo:latest
```

#### mongo-express

Pass in to link the database container with param `--link database-container-name:db` .

```shell
docker run -p 8081:8081 -d --restart always --link mongo:db --name mongo-express mongo-express:latest
```

### Further operations

```shell
# Enter container and initiate shell
docker exec -it mongo sh
```

## Relevent Docker images

- [MongoDB](https://hub.docker.com/_/mongo/)
- [mongo-express](https://hub.docker.com/_/mongo-express/)
