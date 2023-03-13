# Docker guidelines

## `Dockerfile`

When building an image that will be run by one (or many) container(s) providing (the same) services,
use the [`EXPOSE` directive](https://docs.docker.com/engine/reference/builder/#expose)
with mandatory ports only,
to document which ports the services are necessarily listening to. If the image will be used to run many
containers, some of which don't listen on a port, instead use the `expose` option in
`docker-compose.yml` (see the below section for details) or the `--expose` flag to `docker run`.
Some tools ([such as the nginx proxy companion](https://github.com/nginx-proxy/acme-companion#step-3---proxied-containers))
use it to define a contract between different containers too.
Not using this directive doesn’t prevent exposing those ports to the Docker network.

## `docker-compose.yml`

### Exposing ports

By default, containers within the same Docker Compose network are able to connect to services running
on other containers on any port by using the container name, as long as the service running in the
container is listening on `0.0.0.0` which usually is the default too.

The [`expose` configuration option](https://docs.docker.com/compose/compose-file/compose-file-v3/#expose)
just makes this exposure more visible, and is used by
some tools ([such as the nginx proxy companion](https://github.com/nginx-proxy/acme-companion#step-3---proxied-containers))
use it to define a contract between different containers.
Use it to document how your containers are interacting.

### Publishing ports

When publishing the ports of a service in a `docker-compose.yml` file for development, those ports
should be explicitly published to the loopback interface `127.0.0.1` of the host, to prevent docker
from automatically binding them to `0.0.0.0` (all interfaces of the host, open to the world).
Publish ports of a non-public service only if you think it will be necessary for development.
For example, when using `postgres` or `elasticsearch`, we might want to make them available to
developers, but in the case that we deploy on a public server for testing we don't want them to be
open to the world.

Use something like this:

```yaml
ports:
  - "127.0.0.1:5432:5432"
```

In the case of the main HTTP entrypoint to the application, this can be bound to `0.0.0.0`.
