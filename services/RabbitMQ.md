# Guidelines for using RabbitMQ in MetaBrainz projects

Additionally to the [general guidelines for using services](README.md),
here is a list of implementation requirements when using RabbitMQ.
Any deviation from those should be documented.

* [ ] Report connectivity issues through Docker logs and critical connectivity issues through Sentry too.
* [ ] Separate settings for consumer and producer; it allows to smoothly switch to another RabbitMQ instance using shovels.
* [ ] Check for queues declaration before accessing those from both consumer and producer; it prevents getting stuck after switching to a new instance.

If queued messages should not be lost:
* [ ] Document which data might be missing
* [ ] Provide a command to pull/push queued messages to file

In the event the RabbitMQ service is not accessible for some reason, it would prevent producers to queue new messages.
If messages should not be prevented to be queued:
* [ ] Document which data might be missing
* [ ] Provide a plan to produce those messages later on or to deal without those
