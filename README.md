# Useful Docker commands
Collection of commands/scripts for Docker. Listed below are commands I frequently use but often forget the exact syntax for.
#
### Link to Linux
https://github.com/chrxnn/linux
###
### Basic commands
Available commands: start stop restart pause logs
```sh
docker [command] [containername]
```
Show running containers
```sh
docker ps
```
Show docker stats, cpu mem net storage
```sh
docker stats
```
Docker size commands
```
docker system df
docker ps --size
sudo du -h $(docker inspect --format='{{.LogPath}}' $(docker ps -qa)) | sort -hr
````

### Commands for all containers
Pull all new images
```sh
docker images | awk '{print $1":"$2}' | grep -v REPOSITORY | xargs -L1 docker pull 
```
Stop all containers
```sh
docker stop $(docker ps -q)
```
Restart all containers
```sh
docker restart $(docker ps -aq)
```
Print all container names:
```sh
docker ps --format ‘{{.Names}}’
```
Print all container images:
```sh
docker ps --format ‘{{.Image}}’
```

### Docker cleanup
```sh
docker image prune -a
docker system prune --volumes
```

### Convert running docker to compose
```
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/red5d/docker-autocompose CONTAINERNAME >> CONTAINERNAME.yml
```
