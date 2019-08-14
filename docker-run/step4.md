## Run Containers

The docker run command can be used to create a runtime instance of an image (i.e. container).

`docker run --help`{{execute}}

```
$ docker run --help

Usage:    docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

Run a command in a new container
```

All containers are executed with a command. This command may be the default one defined by the image if the user does not specify any.

Let's run the hello-world image with the default command and no options:

## View containers

To list the containers that currently exist in our host we use docker ps.

`docker ps --help`{{execute}}

```
$ docker ps --help

Usage:    docker ps [OPTIONS]

List containers
```

## Remove containers

How can we remove the hello-world container that is currently stopped? By using docker rm.

`docker rm --help`{{execute}}

```
$ docker rm --help

Usage:    docker rm [OPTIONS] CONTAINER [CONTAINER...]

Remove one or more containers
```


We need to get the container ID or name from docker ps and then run this command:

docker rm <container_id_or_name>
