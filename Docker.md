## development docker-compose.yaml file

### Publishing ports

Ports for services should be explicitly published to the loopback interface, 127.0.0.1 to prevent docker from binding them to 0.0.0.0.
For example, when using postgres or elasticsearch, we might want to make them available to developers, but in the case that we deploy on a public server for testing we don't want them to be exposed.

Use something like this:

```yaml
ports:
  - "127.0.0.1:5432:5432"
```

In the case of the main HTTP entrypoint to the application, this can be bound to 0.0.0.0.
