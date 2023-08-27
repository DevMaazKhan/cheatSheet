# Docker

## Docker version

Get docker version details and some other information about the current docker installed version.

## Docker info

Get in depth information on docker, information on the current state of docker, and more

# Docker Commands

Docker has 2 types of commands

- simple commands
- management commands

management commands, are the parent commands of simple commands
docker container run

in this case container is the management commands and run is simple command

## Docker container run <options> <image-name> <container-start-command>

this command is used to run a container process in docker

eg: docker container run --name enginex --port 80:8080 --detach nginx

### Options

- --name
  this option is used to define the name of the container
- --publish
  this option is used to mark a forward port, requests to the given port will be forwarded to the containers port
- --detach
  this options is used to run the container, in detach mode

## Docker container start <container-name>

this command is used to start a container process, a container that already exists

## Docker container stop <container=name>

this command is used to stop a running container

## Docker container ls

list all running containers

## Docker container ls -a

list all containers
