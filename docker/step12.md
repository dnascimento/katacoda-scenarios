## Devs vs Ops, before Docker

* Drop a tarball (or a commit hash) with instructions.

* Dev environment very different from production.

* Ops don't always have a dev environment themselves ...

* ... and when they do, it can differ from the devs'.

* Ops have to sort out differences and make it work ...

* ... or bounce it back to devs.

* Shipping code causes frictions and delays.

---

## Devs vs Ops, after Docker

* Drop a container image or a Compose file.

* Ops can always run that container image.

* Ops can always run that Compose file.

* Ops still have to adapt to prod environment,
  but at least they have a reference point.

* Ops have tools allowing to use the same image
  in dev and prod.

* Devs can be empowered to make releases themselves
  more easily.
