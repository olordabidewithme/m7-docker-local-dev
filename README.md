Demo Project:
Docker for local development

Technologies used:
Docker, Node.js, MongoDB, MongoExpress

Project Description:
Run Node.js application locally.
Run MongoDB database container locally.
Also run MongoExpress container as a UI for the database.

Create Network
```bash
docker network create mongo-network
```

Run MongoDB Container

```bash
docker run -d \
-p 27017:27017 \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=password \
--name mongodb \
--net mongo-network \
mongo
```
Run Mongo Express

```bash
docker run -d \
--network mongo-network \
--name mongo-express \
-p 8081:8081 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
-e ME_CONFIG_BASICAUTH_USERNAME=user \
-e ME_CONFIG_BASICAUTH_PASSWORD=pass \
-e ME_CONFIG_MONGODB_URL=mongodb://mongodb:27017 \
mongo-express
```

