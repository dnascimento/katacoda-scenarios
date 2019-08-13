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
