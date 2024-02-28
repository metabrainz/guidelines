# Guidelines for using RabbitMQ in MetaBrainz projects

Additionally to the [general guidelines for using services](README.md),
here is a list of implementation requirements when using RabbitMQ.
Any deviation from those should be documented.

* [ ] Report connectivity issues through Docker logs and critical connectivity issues through Sentry too.
* [ ] Separate settings for consumer and producer; it allows to smoothly switch to another RabbitMQ instance using shovels.
  And to help with debugging, read the following parameters (not limited to) from settings:
  * [ ] Acknowledgement mode (manual or automatic)
  * [ ] Heartbeat timeout (if different from server’s default)
  * [ ] Message protocol (AMQP 0-8, AMQP 0-9-1, AMQP 1.0, MQTT...)
* [ ] Check for queues declaration before accessing those from both consumer and producer; it prevents getting stuck after switching to a new instance.
* [ ] Name each connection with project and role so those can be individually identified in the RabbitMQ admin console.

If queued messages should not be lost:
* [ ] Document which data might be missing
* [ ] Provide a command to pull/push queued messages to file

In the event the RabbitMQ service is not accessible for some reason, it would prevent producers to queue new messages.
If messages should not be prevented to be queued:
* [ ] Document which data might be missing
* [ ] Provide a plan to produce those messages later on or to deal without those

## Examples

* Documentation page “[LB > Maintainer Documentation > RabbitMQ](https://listenbrainz.readthedocs.io/en/latest/maintainers/rabbitmq.html)”
  (still in development branch) <!-- TODO: replace /latest/ with /stable/ on release -->

* Documentation page “[SIR > Service maintenance > RabbitMQ](https://sir.readthedocs.io/en/latest/service/index.html#rabbitmq-1)”
  (still in development branch) <!-- TODO: replace /latest/ with /stable/ on release -->

Look for [not closed tickets](https://tickets.metabrainz.org/issues/?jql=labels+=+rabbitmq-service-guidelines+AND+status+!=+Closed),
with `rabbitmq-service-guidelines` label, and create missing ones
for projects which are using RabbitMQ without following these guidelines.
