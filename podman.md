# Podman Notes and setup

## Storage
* Podman's Local (Common) Repository - /var/lib/containers
* User's Repository - ~/.local/share/containers

## Useful flags
* -all - 

## Container Registries
* docker hub
* Quay.io
* nexus.wildcardcorp.com

### Local Registries
registries.conf - modifiy this to look at nexus.wildcardcorp.com first

### Pull repository from docker to podman 
``` sh
$ podman pull docker-daemon:myrepo:version
```
## Kubernetes Commands
``` sh
$ podman generate kebe
$ podman pod
```
# Buildah - superset of podman build
Commands are not 100% like podman's.  Used for creating the image.
* Try to run as a container on k8s
