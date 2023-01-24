# Project Setup

How I set up my projects.

## Tips

### General

- If the app has to do with valuable assets such as money or identity, then consider building a dApp instead of an app.
- Always use open source technologies over vendor specific ones (e.g., Grafana instead of Amazon CloudWatch,
  OpenTelemetry instead of Sentry) because they're cheaper, have more features, works in more places (they work locally,
  and can be connected to via a different hosting solution even if your server's hosting solution doesn't support it),
  and removes the need for migrations (e.g., Amazon CloudWatch alerts will have to be rewritten if you migrate to GCP
  but not if you were using Grafana).
- Create a mantra (slogan). Use two to four words to describe why your product should exist. For example, "Healthy fast
  food" for Wendy's, "Authentic athletic performance" for Nike. It needs to be this short. Otherwise, it won't fit on
  branding assets, and it won't be very memorable or meaningful.
- You can generate a free logo using [hatchful](https://hatchful.shopify.com/). Don't
  use [namecheap](https://www.namecheap.com/logo-maker/)'s or [fiverr](https://www.fiverr.com/logo-maker)'s because
  they're buggy, average, and/or have watermarks.
- Tips on naming projects:
  - Watch this [video](https://www.youtube.com/watch?v=4CaB_dSMHcU).
  - The easiest names that sound the best are two words. The first word is related to the project, and the second is the
    name of a dessert or animal. If you're picking an animal, choose something interesting like the Purple Queen
    Anthias. The first letter (preferably the first two letters) of both words must be the same. For example, the
    project _Blockchain Node Fallback System_ can be named _Fallback Falooda_, and the project _Transaction Ingester_
    can be named _Transaction Truffle_.
  - A combination of a tasty food, and cool concept. For example, Space Flan, Space Sausages, Jurassic Jalebi, Jurassic
    Tacos, Triassic Tacos, and Nuclear Naan.
  - Something based on your favorite fictions. For example, the ansible from Ender’s Game.
  - A combination of good names. For example, prototype + byte = ProtoByte.
  - A superhero or super villain.
  - The name you've thought of translated to Latin, Hindi, Greek, Spanish, Italian, French, or Japanese
  - A biology term
  - Ether, or its translation in another language.
  - Olympics/Olympia/Olympion
  - The Dragon Scroll
  - Cyclops, gremlin, ghost, goblin, etc.
  - Fictional/non-fictional character good at that particular thing. For example, Mazer Rackham: good heart but
    merciless at enemies, Bean: small but brilliant, a transformer such as Bumblebee who speaks randomly yet on-topic.
  - The name of a god who's good at the problem you're solving such as Apollo for transportation.

### Backend

- To implement the equivalent of a cron job, you can use RabbitMQ with
  the [RabbitMQ Delayed Message Plugin](https://github.com/rabbitmq/rabbitmq-delayed-message-exchange) and
  the [RabbitMQ Message Deduplication Plugin](https://github.com/noxdafox/rabbitmq-message-deduplication). The latter is
  required because the `max-length` and `x-max-length` arguments on queues aren't honored when using the RabbitMQ
  Delayed Message Plugin. On a side note,
  the [RabbitMQ Message Deduplication Plugin](https://github.com/noxdafox/rabbitmq-message-deduplication/issues/80#issuecomment-1361307712)
  doesn't work if the messages are sent very close to each other such as during the same millisecond.

## Tools

- [System administration](system-administration.md)
- [Kotlin/JVM backend](kotlin-jvm-backend.md)
- [Node.js backend](node-js-backend.md)
- [Frontend web](frontend-web.md)

## Contributing

When updating a technology's entry, update it wherever else it's written about too. For example, there's a section of
VCSes in both the [System Administration](system-administration.md) and [JVM Backend](kotlin-jvm-backend.md) docs.

## License

This project is under the [MIT License](LICENSE).
