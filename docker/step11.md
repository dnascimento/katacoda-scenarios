## Elevator pitch

### (for your fellow devs and ops)

## Escape dependency hell

1. Write installation instructions into an `INSTALL.txt` file

2. Using this file, write an `install.sh` script that works *for you*

3. Turn this file into a `Dockerfile`, test it on your machine

4. If the Dockerfile builds on your machine, it will build *anywhere*

5. Rejoice as you escape dependency hell and "works on my machine"

Never again "worked in dev - ops problem now!"

## On-board developers and contributors rapidly

1. Write Dockerfiles for your application components

2. Use pre-made images from the Docker Hub (mysql, redis...)

3. Describe your stack with a Compose file

4. On-board somebody with two commands:

```bash
git clone ...
docker-compose up
```

With this, you can create development, integration, QA environments in minutes!

---

## Implement reliable CI easily

1. Build test environment with a Dockerfile or Compose file

2. For each test run, stage up a new container or stack

3. Each run is now in a clean environment

4. No pollution from previous tests

Way faster and cheaper than creating VMs each time!

---

## Use container images as build artefacts

1. Build your app from Dockerfiles

2. Store the resulting images in a registry

3. Keep them forever (or as long as necessary)

4. Test those images in QA, CI, integration...

5. Run the same images in production

6. Something goes wrong? Rollback to previous image

7. Investigating old regression? Old image has your back!

Images contain all the libraries, dependencies, etc. needed to run the app.

---

## Formats and APIs, before Docker

* No standardized exchange format.
  <br/>(No, a rootfs tarball is *not* a format!)

* Containers are hard to use for developers.
  <br/>(Where's the equivalent of `docker run debian`?)

* As a result, they are *hidden* from the end users.

* No re-usable components, APIs, tools.
  <br/>(At best: VM abstractions, e.g. libvirt.)

Analogy:

* Shipping containers are not just steel boxes.
* They are steel boxes that are a standard size, with the same hooks and holes.

## Formats and APIs, after Docker

* Standardize the container format, because containers were not portable.

* Make containers easy to use for developers.

* Emphasis on re-usable components, APIs, ecosystem of standard tools.

* Improvement over ad-hoc, in-house, specific tools.

---
## Shipping, before Docker

* Ship packages: deb, rpm, gem, jar, homebrew...

* Dependency hell.

* "Works on my machine."

* Base deployment often done from scratch (debootstrap...) and unreliable.

---
## Shipping, after Docker

* Ship container images with all their dependencies.

* Images are bigger, but they are broken down into layers.

* Only ship layers that have changed.

* Save disk, network, memory usage.
