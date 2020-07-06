## Compose sample application
### Nodebb

Project structure:
```
.
├── docker-compose.yaml
├── README.md

```

The compose file defines an application with two services `nodebb` and `db`.
When deploying the application, docker-compose maps port 4567 of the web service container to port 4567 of the host as specified in the file.
Make sure port 4567 on the host is not already being in use.

More info on Nodebb https://github.com/NodeBB/NodeBB

## Deploy with docker-compose

```
$ docker-compose up -d
Starting nodebb_db_1 ... done
Creating nodebb_nodebb_1 ... done
```

## Expected result

Listing containers must show two containers running and the port mapping as below:
```
$ docker ps
CONTAINER ID        IMAGE                  COMMAND                  CREATED              STATUS              PORTS                      NAMES
ff13a30d327a        nodebb/docker:latest   "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:4567->4567/tcp     nodebb_nodebb_1
db10cb49ad2a        mongo:bionic           "docker-entrypoint.s…"   12 minutes ago       Up About a minute   0.0.0.0:27017->27017/tcp   nodebb_db_1
```

After the application starts, navigate to `http://0.0.0.0:4567` in your web browser.


Stop and remove the containers
```
$ docker-compose down
Removing nodebb_nodebb_1 ... done
Removing nodebb_db_1     ... done
Removing network nodebb_default
```
