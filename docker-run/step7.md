# Write a Dockerfile

Up until this point we've created a web server container and run some commands in an interactive shell inside it. What happens if we need to replicate or regenerate the container? Do we need to manually run all those commands again?

One of the main principles of Docker is that containers must be ephemeral, which means that the regeneration cost must be minimal. Having to run a bunch of commands each time we create a container goes against this.

The answer is writing a *Dockerfile*. This file is basically a recipe, a set of instructions that will be run in order to create a custom Docker image.

The following set of instructions represent a *Dockerfile* to encapsulate the actions of the previous step.

```
FROM nginx
RUN apt-get update && apt-get install -y wget
WORKDIR /usr/share/nginx/html/
RUN wget -O image.png http://lorempixel.com/300/200/animals/
```

> For convenience the *Dockerfile* may be downloaded from a public URL:

`curl -O https://raw.githubusercontent.com/agmangas/katacoda-scenarios/master/intro-containers-lab-01/Dockerfile`{{execute}}

# Build an image

Let's build a custom image named *custom-nginx* using the `docker build` command:

`docker build -t nginx-custom .`{{execute}}

> Note that this command must be run in the same level as the *Dockerfile* file.

We may verify that the recently created image is in our system by using `docker images`{{execute}} to list all the images.

Now we can create as many containers as we like from our custom image:

`docker run -d -p 9292:80 --name another_server nginx-custom`{{execute}}

Check that our new server is working by accessing the URL:

`http://<hostname>:9292/image.png`
