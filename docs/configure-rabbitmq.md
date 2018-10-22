# Configure RabbitMQ
The Service RabbitMQ is already available in this environment, but not loaded by default.
To load RabbitMQ, simply add a `conf/rabbitmq` file with these variables:

```
RABBITMQ_ERLANG_COOKIE=SWQOKODSQALRPCLNMEQG
RABBITMQ_DEFAULT_USER=YOUR_USERNAME
RABBITMQ_DEFAULT_PASS=YOUR_PASSWORD
RABBITMQ_DEFAULT_VHOST=/
```

To access the RabbitMQ Management, just access from browser: http://rabbitmq.localhost (use our username and password configured in `conf/rabbitmq` to access).

If you have any question, access the [Official Repository][1]

[1]: https://hub.docker.com/_/rabbitmq/
