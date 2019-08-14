# Running a Web server
## Background web server container

The hello-world container was short-lived and executed in foreground. Docker may also be used to run background services like a Web server.

`docker run -d -p 9191:80 --name web_server nginx`{{execute}}

If we access port 9191 of our host machine after executing the previous command we'll see the Nginx web server welcome page.

Let's break that command into parts:

- `-d` runs the container in background.
- `-p 9191:80` exposes internal port 80 of the container in port 9191 of the host - machine.
- `--name web_server` specifies the name of the container as web_server.
- `nginx` runs a container using the nginx image with the default command.

## Internal access to the container

We now want to access an interactive shell in our running web server container.

By using the docker exec command we may run a new command in a running container:

`docker exec -it web_server bash`{{execute}}

Note that all commands executed with docker exec are tied to the container's primary process and will be killed if the container stops.

Let's get some new static content to host in our web server by running the following commands inside the container:

`echo "<h3>hello</h3>" > /usr/share/nginx/html/hello.html`{{execute}}

We've downloaded a new image named image.png to our web server root directory. We can view that image by going to:

`curl http://<hostname>:9191/hello.html`{{execute}}
