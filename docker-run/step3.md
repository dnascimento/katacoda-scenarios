## A more useful container

Let's run a more exciting container:

(on your laptop: **docker.artifactory.ai.cba/library/ubuntu**)

`docker run -it ubuntu`{{execute}}

* This is a brand new container.

* It runs a bare-bones, no-frills `ubuntu` system.

* `-it` is shorthand for `-i -t`.

  * `-i` tells Docker to connect us to the container's stdin.

  * `-t` tells Docker that we want a pseudo-terminal.

## Do something in our container

Try to run `figlet` in our container.

`figlet`{{execute}}

```bash
root@04c0bb0a6c07:/# figlet hello
bash: figlet: command not found
```

Alright, we need to install it.

---

## Install a package in our container

We want `figlet`, so let's install it:

`apt-get update; apt-get install -y figlet`{{execute}}

One minute later, `figlet` is installed!

---

## Try to run our freshly installed program

The `figlet` program takes a message as parameter.

`figlet hello`{{execute}}

```bash
root@04c0bb0a6c07:/# figlet hello
 _          _ _
| |__   ___| | | ___
| '_ \ / _ \ | |/ _ \
| | | |  __/ | | (_) |
|_| |_|\___|_|_|\___/
```

Beautiful! .emoji[😍]
