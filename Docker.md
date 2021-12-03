## development docker-compose.yaml file

### Publishing ports

By default, containers within the same docker-compose network are able to connect to services running
on other containers on any port by using the container name, as long as the container is listening
on 0:0:0:0.

The [`EXPOSE` directive isn't needed](https://docs.docker.com/engine/reference/builder/#expose), although
some tools ([such as the nginx proxy companion](https://github.com/nginx-proxy/acme-companion#step-3---proxied-containers))
use it to define a contract between different containers. Use it if you think it will be necessary.

When publishing services in a docker-compose.yaml file, ports should be explicitly published to the
loopback interface, 127.0.0.1 to prevent docker from automatically binding them to 0.0.0.0
(all interfaces, open to the world).
For example, when using postgres or elasticsearch, we might want to make them available to developers, 
but in the case that we deploy on a public server for testing we don't want them to be exposed.

Use something like this:

```yaml
ports:
  - "127.0.0.1:5432:5432"
```

In the case of the main HTTP entrypoint to the application, this can be bound to 0.0.0.0.
