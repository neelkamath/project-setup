# Node.js Backend

- JVM backends are superior but this section exists because I have experience with these technologies, and might need to
  use them as a reference in the future if I'm ever forced to use Node.js on the backend again (such as for work).
- Here's a [template](https://github.com/neelkamath/node-js-template) for a microservice.
- Here's a [template](https://github.com/neelkamath/js-lib-template) for a Node.js library.

## Programming Language

[TypeScript](https://www.typescriptlang.org/)

Kotlin might be superior, but I'm not sure because I haven't tried Kotlin for Node.js.

<details>
<summary>Reason</summary>

- Flow doesn't have as much support.
- JavaScript isn't statically typed.

</details>

## Message Broker

[RocketMQ](https://rocketmq.apache.org/) is better but [Kafka](https://kafka.apache.org/)
/[RabbitMQ](https://www.rabbitmq.com/) can be used instead in case RocketMQ isn't available as a SaaS, etc.

<details>
<summary>Reason</summary>

- RocketMQ is faster than Kafka and RabbitMQ.
- RocketMQ is easier to use. Though RabbitMQ supports advanced routing, it's difficult to use even for basic use cases.
  RocketMQ is easy to use but support advanced usage because it has a query language like SQL.
- RabbitMQ is buggy. For example, the `max-length` and `x-max-length` arguments on queues aren't honored when using
  the [RabbitMQ Delayed Message Plugin](https://github.com/rabbitmq/rabbitmq-delayed-message-exchange), and
  the [RabbitMQ Message Deduplication Plugin](https://github.com/noxdafox/rabbitmq-message-deduplication/issues/80#issuecomment-1361307712)
  doesn't work if the messages are sent very close to each other such as during the same millisecond.
- While RabbitMQ depends on buggy third party plugins to achieve basic functionality, RocketMQ supports such
  functionality out of the box.

</details>

## VCS

[GitHub](https://github.com/)

<details>
<summary>Reason</summary>

- GitHub has an issue tracking system, CI/CD pipelines, etc. which are better than competitors' such as GitLab and
  BitBucket in terms of UI/UX and stability.

</details>

## Observability

### Telemetry Library

[OpenTelemetry](https://opentelemetry.io/)

<details>
<summary>Reason</summary>

- It's the industry standard.
- The same library can be used for logs, traces, and metrics.
- It has auto instrumentation for Redis, Postgres, RabbitMQ, etc.
- It allows you to easily switch to a different observability backend since it's vendor-agnostic. For example, you can
  switch from Jaeger to Zipkin or Tempo without much effort.

</details>

### Telemetry Agent

[Grafana Agent](https://github.com/grafana/agent)

<details>
<summary>Reason</summary>

- The same agent can be used for logs, traces, and metrics. You only need to install one binary, and one create one
  configuration file. Otherwise, you'd need to set up Prometheus just for metrics, etc. It also takes up less resources
  than just Prometheus because it doesn't contain useless parts such as a charting webpage.

</details>

### Log Format

[The Syslog Protocol](https://datatracker.ietf.org/doc/html/rfc5424)

<details>
<summary>Reason</summary>

- It's the industry standard.

</details>

### HTTP Request Logging Middleware

[Morgan](https://github.com/expressjs/morgan)

### Logs Backend

[Loki](https://grafana.com/oss/loki/)

<details>
<summary>Reason</summary>

- Part of the LGTM stack which allows you to cheaply and efficiently correlate logs, traces, and metrics across multiple
  services in a single dashboard.

</details>

### Traces Backend

[Tempo](https://grafana.com/oss/tempo/)

<details>
<summary>Reason</summary>

- Part of the LGTM stack which allows you to cheaply and efficiently correlate logs, traces, and metrics across multiple
  services in a single dashboard.

</details>

### Metrics Backend

[Prometheus](https://prometheus.io/)

- Use it with every supported integration such as [Caddy](https://caddyserver.com/docs/metrics)
  , [containers](https://github.com/google/cadvisor), and [Linux](https://prometheus.io/docs/guides/node-exporter/).
- Use Prometheus tools but don't install Prometheus itself - use Grafana Agent to transport telemetry.

<details>
<summary>Reason</summary>

- Part of the LGTM stack which allows you to cheaply and efficiently correlate logs, traces, and metrics across multiple
  services in a single dashboard.

</details>

### Visualizations

[Grafana](https://grafana.com/grafana/)

<details>
<summary>Reason</summary>

- Part of the LGTM stack which allows you to cheaply and efficiently correlate logs, traces, and metrics across multiple
  services in a single dashboard.

</details>

### Alerts

[Grafana OnCall](https://grafana.com/products/oncall/)

- Use phone calls for urgent alerts.
- Use Slack if you're in a team, and email otherwise for non-urgent alerts.

<details>
<summary>Reason</summary>

- Integrates with monitoring tools such as logs, traces, and metrics (Prometheus, etc.).
- Affordable (unlimited free phone call alerts, etc.).

</details>

### Hosting

[Grafana Cloud](https://grafana.com/products/cloud/)

<details>
<summary>Reason</summary>

- It's better to us a SaaS than to host it yourself.
- They have a 50 GB free forever plan with no billing details required.

</details>

## Changelog

[Keep a Changelog](https://github.com/olivierlacan/keep-a-changelog)

## Containerization

[Docker](https://www.docker.com/)

<details>
<summary>Reason</summary>

- It has the most support since it's the industry standard.

</details>

## Caching

### Backend

[Ignite](https://ignite.apache.org/)

<details>
<summary>Reason</summary>

- It's faster than Redis because it can additionally store the data locally.
- It's easier to use than Redis because Redis requires a cache-aside pattern while Ignite uses the read/write-through
  pattern.
- Redis has other features such as a database, but they're terrible. Ignite's extra features are great (ML APIs, etc.).
- Redis cannot be practically clustered because it'll lose consistency, requires third party tools, requires manual
  intervention, and doesn't support certain operations in clustered mode. Ignite can be replicated, and still support
  distributed ACID transactions.
- Querying is easier in Ignite when compared to Redis because it uses SQL.
- Redis cannot be practically sharded. It'll lose consistency, and/or requires manual intervention. Ignite can partition
  data seamlessly.
- It's better than Hazelcast because it's consistent but can also be available if explicitly told to (consistent and
  available refer to the CAP theorem).

</details>

### Redis Library

[ioredis](https://github.com/luin/ioredis)

<details>
<summary>Reason</summary>

- The official Redis library for Node.js is buggy (incorrect type definitions, etc.).

</details>

## API

### Layer

[GraphQL](https://graphql.org/)

<details>
<summary>Reason</summary>

- Larger APIs need GraphQL. Medium-sized APIs may eventually need GraphQL. So, it's better to start off with it because
  rewriting the entire API layer later on will take a very long time. Even smaller APIs should use GraphQL because the
  overhead of using it is worth the benefits of static typing (input validation, clients know how to deserialize
  responses because of the `__typename` field, etc.).

</details>

### Input Validation

[joi](https://github.com/sideway/joi)

### REST API Specification

[OpenAPI](https://openapis.org/)

<details>
<summary>Reason</summary>

- It's the industry standard.
- It generates a documentation site that contains a playground.
- It doesn't require installing any desktop apps, etc. like Postman does.
- It can generate API wrapper libraries in any language.
- It can generate a mock server to speed up development of clients while the actual backend is getting built.

</details>

### REST/WebSocket Linter

[Spectral](https://github.com/stoplightio/spectral)

### REST API Wrapper Library Generator

[OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator)

### REST API Docs Generator

[RapiDoc](https://mrin9.github.io/RapiDoc/)

<details>
<summary>Reason</summary>

- The next best one is ReDoc but that doesn't have a builtin playground.

</details>

### REST API Mock Server

[Prism](https://github.com/stoplightio/prism)

### WebSocket API Spec

[AsyncAPI](https://www.asyncapi.com/)

<details>
<summary>Reason</summary>

- It's the industry standard.

</details>

### WebSocket API Wrapper Library Generator

[AsyncAPI Generator](https://github.com/asyncapi/generator#cli-usage-with-npx-instead-of-npm)

### WebSocket API Mock Server

[Microcks](https://microcks.io/)

### Tunneling

[ngrok](https://ngrok.com/)

## DB

### Relational DB

[CockroachDB](https://www.cockroachlabs.com/)

<details>
<summary>Reason</summary>

- A production system mandates replication, even if it's just a read replica which gets upgraded to a master when the
  master goes down. Postgres cannot be practically clustered because it's inconsistent by default when replicated.
  CockroachDB uses a consensus algorithm to prevent inconsistencies when being replicated.
- Postgres cannot be practically partitioned as it requires manual intervention. CockroachDB natively supports sharding.

</details>

### Graph DB

[Neo4j](https://neo4j.com/)

Any data can be easily and efficiently stored in a graph. However, a graph cannot be stored as any other data structure.
Therefore, graph databases are better than relational ones. However, since they can't be practically partitioned (they
lose consistency when sharded), relational databases should be used by default. If you need a graph, and don't need
partitioning, then use Neo4j.

<details>
<summary>Reason</summary>

- OrientDB doesn't use a graph query language which removes a major use case of graph databases.
- TigerGraph isn't battle tested, and is close sourced.
- It has the most support.

</details>

## Testing

### Framework

[Jest](https://jestjs.io/)

<details>
<summary>Reason</summary>

- It's a single framework has a mocking API, test runner, and assertions.

</details>

### Dependency Injection

[TypeDI](https://docs.typestack.community/typedi/01-getting-started)

<details>
<summary>Reason</summary>

- Easy to learn and use.

</details>

### Testing APIs

[Supertest](https://www.npmjs.com/package/supertest)

## Automatic Dev Server Reloading

[nodemon](https://nodemon.io/)

## Web Framework

[Express](http://expressjs.com/)

<details>
<summary>Reason</summary>

- The standard library is too low level, and not recommended to create a web server.
- Frameworks such as Koa do basically nothing - you might as well just use the standard library.
- Other frameworks are too opinionated.

</details>

## Package Manager

[npm](https://www.npmjs.com/)

<details>
<summary>Reason</summary>

- Yarn is not supported nearly as much such as the docs to publish private npm packages.
- All of Yarn's features have been copied over to npm.
- Yarn requires more work (must be installed separately while npm is installed automatically with Node.js, etc.).

</details>

## Linting

[ESLint](https://eslint.org/)

<details>
<summary>Reason</summary>

- It's the industry standard.

</details>

## Formatting

[Prettier](https://prettier.io/)

<details>
<summary>Reason</summary>

- It supports multiple languages.
- It's easy to use (good defaults, no excessive configuration options, etc.).

</details>

## HTTP Requests

[cross-fetch](https://github.com/lquixada/cross-fetch)

<details>
<summary>Reason</summary>

- Available as a ponyfill.
- Supports Node.js and React Native.

</details>
