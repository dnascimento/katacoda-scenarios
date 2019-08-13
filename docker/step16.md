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
