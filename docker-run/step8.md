## `Dockerfile`

* A `Dockerfile` is a build recipe for a Docker image.

* It contains a series of instructions telling Docker how an image is constructed.

* The `docker build` command builds an image from a `Dockerfile`.

## Writing our first `Dockerfile`

Our Dockerfile must be in a **new, empty directory**.

1. Create a directory to hold our `Dockerfile`.

`mkdir myimage`{{execute}}


1. Create a `Dockerfile` inside this directory.

`cd myimage`{{execute}}
`vim Dockerfile`{{execute}}

Of course, you can use any other editor of your choice.

---

## Type this into our Dockerfile...

```dockerfile
FROM ubuntu
RUN apt-get update
RUN apt-get install figlet
```{{copy}}

* `FROM` indicates the base image for our build.

* Each `RUN` line will be executed by Docker during the build.

* Our `RUN` commands **must be non-interactive.**
  <br/>(No input can be provided to Docker during the build.)

* In many cases, we will add the `-y` flag to `apt-get`.

---

## Build it!

Save our file, then execute:

`docker build -t figlet .`{{execute}}

* `-t` indicates the tag to apply to the image.

* `.` indicates the location of the *build context*.

We will talk more about the build context later.

To keep things simple for now: this is the directory where our Dockerfile is located.

---

## What happens when we build the image?

The output of `docker build` looks like this:

```bash
docker build -t figlet .
Sending build context to Docker daemon  2.048kB
Step 1/3 : FROM ubuntu
 ---> f975c5035748
Step 2/3 : RUN apt-get update
 ---> Running in e01b294dbffd
(...output of the RUN command...)
Removing intermediate container e01b294dbffd
 ---> eb8d9b561b37
Step 3/3 : RUN apt-get install figlet
 ---> Running in c29230d70f9b
(...output of the RUN command...)
Removing intermediate container c29230d70f9b
 ---> 0dfd7a253f21
Successfully built 0dfd7a253f21
Successfully tagged figlet:latest
```


* The output of the `RUN` commands has been omitted.
* Let's explain what this output means.

---

## Sending the build context to Docker

```bash
Sending build context to Docker daemon 2.048 kB
```

* The build context is the `.` directory given to `docker build`.

* It is sent (as an archive) by the Docker client to the Docker daemon.

* This allows to use a remote machine to build using local files.

* Be careful (or patient) if that directory is big and your link is slow.

* You can speed up the process with a [`.dockerignore`](https://docs.docker.com/engine/reference/builder/#dockerignore-file) file

  * It tells docker to ignore specific files in the directory

  * Only ignore files that you won't need in the build context!
---

## Running the image

The resulting image is not different from the one produced manually.

`docker run -ti figlet`{{execute}}

```bash
$ docker run -ti figlet
root@91f3c974c9a1:/# figlet hello
 _          _ _
| |__   ___| | | ___
| '_ \ / _ \ | |/ _ \
| | | |  __/ | | (_) |
|_| |_|\___|_|_|\___/
```


Yay! .emoji[🎉]
