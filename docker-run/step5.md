## Host and containers are independent things

* We ran an `ubuntu` container on an Linux/Windows/macOS host.

* They have different, independent packages.

* Installing something on the host doesn't expose it to the container.

* And vice-versa.

* Even if both the host and the container have the same Linux distro!

* We can run *any container* on *any host*.

  (One exception: Windows containers cannot run on Linux machines; at least not yet.)
---

## Where's our container?

* Our container is now in a *stopped* state.

* It still exists on disk, but all compute resources have been freed up.

* We will see later how to get back to that container.

---

## Starting another container

What if we start a new container, and try to run `figlet` again?

`docker run -it ubuntu`{{execute}}

```bash
$ docker run -it ubuntu
root@b13c164401fb:/# figlet
bash: figlet: command not found
```

* We started a *brand new container*.

* The basic Ubuntu image was used, and `figlet` is not here.

---

## Where's my container?

* Can we reuse that container that we took time to customize?

  *We can, but that's not the default workflow with Docker.*

* What's the default workflow, then?

  *Always start with a fresh container.*
  <br/>
  *If we need something installed in our container, build a custom image.*

* That seems complicated!

  *We'll see that it's actually pretty easy!*

* And what's the point?

  *This puts a strong emphasis on automation and repeatability. Let's see why ...*

---

## Pets vs. Cattle

* In the "pets vs. cattle" metaphor, there are two kinds of servers.

* Pets:

  * have distinctive names and unique configurations

  * when they have an outage, we do everything we can to fix them

* Cattle:

  * have generic names (e.g. with numbers) and generic configuration

  * configuration is enforced by configuration management, golden images ...

  * when they have an outage, we can replace them immediately with a new server
