
## Running Docker on macOS and Windows

**IMPORTANT:**
- Public containers must be prefixed with: **dockerhub.artifactory.ai.cba**
- Private containers are stored in **docker.artifactory.ai.cba**

### OSX
- [Installer](https://download.docker.com/mac/stable/Docker.dmg)
- [Info](https://docs.docker.com/v17.12/docker-for-mac/install/)

### Windows
- [Installer](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)
- [Info](https://docs.docker.com/v17.12/docker-for-windows/install/#download-docker-for-windows)

## Testing

When you execute `docker version`{{execute}} from the terminal:

* the CLI connects to the Docker Engine over a standard socket,
* the Docker Engine is, in fact, running in a VM,
* ... but the CLI doesn't know or care about that,
* the CLI sends a request using the REST API,
* the Docker Engine in the VM processes the request,
* the CLI gets the response and displays it to you.

All communication with the Docker Engine happens over the API.

This will also allow to use remote Engines exactly as if they were local.
