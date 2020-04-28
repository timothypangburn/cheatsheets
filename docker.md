## Build an Image
#### Builds an images from the Dockerfile in `.` with the <repo> name and <tag> using the -t
$ docker build -t repo:tag .

## Build (Run) a Container
-d - detached mode
-p - set the port forwarding - <container>:<host>
--name - sets the name of the container 
--network - set what network you want the container to attach too
--uts - the UTS namespace is for setting the hostname and the domain that is visible to running processes in that namespace
--ip - set the IP
--ip6 - set the IPv6
--restart - restart the container 
--memory-swappiness - how much swap the container should use. ( 0 for elasticsearch servers)
\# docker run -d 9200:9200 --name <image name> 
$ docker run -p 9200:9200 -p 9300:9300 --name=fg20_es23 --memory-swappiness=0 --volume="fg20es23-data-vol:/data/fg20es23:rw" wildcardcorp:elasticsearch2.3.5
## Build a Volume for Docker
$docker volume create <volume-name>
Do the following to make sure docker can access and use the volume.
$ docker inspect <volume-name>
$ chmod -R g+rwx <Mountpoint>
Add user to correct group.
##Build Network for Docker Containers
docker network create -d bridget network-name
###List Networks
docker network ls
### Inspect or view containers on a network
docker inspect network-name

## Build a Config for Docker Containers (requires Swarm service)
docker config create
docker config inspect
docker config ls
docker config rm

$ docker run -d -p 9200:9200 --volume="fg20es23-data-vol:/data/fg20es23:rw" wildcard:elasticsearch2.3

### Docker Connect to a Container with Bash
docker exec -it container-name /bin/bash
