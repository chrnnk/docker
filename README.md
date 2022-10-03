## Useful Docker commands
Collection of commands/scripts for Docker. Listed below are commands I frequently use but often forget the exact syntax for.

#### Link to Linux
https://github.com/chrxnn/linux

#### Show running
```sh
docker ps
```

#### Show docker stats, cpu mem net storage
```sh
docker stats
```

#### Stop all containers
```sh
docker stop $(docker ps -q)
```

#### Restart all containers
```sh
docker restart $(docker ps -aq)
```

#### Pull all new images
```sh
docker images | awk '{print $1":"$2}' | grep -v REPOSITORY | xargs -L1 docker pull 
```


#### Prune old images
```sh
docker image prune -a
```

## Docker containers

#### Basic commands

```sh
docker [command] [containername]
```
Available commands: start stop restart pause logs

#### Print all container names:

```sh
docker ps --format ‘{{.Names}}’
```
#### Print all container images:

```sh
docker ps --format ‘{{.Image}}’
```
