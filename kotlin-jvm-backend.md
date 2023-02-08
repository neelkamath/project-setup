# Kotlin/JVM Backend

<details>
<summary>Reason</summary>

- Kotlin has the largest backend ecosystem. For example:
  - RocketMQ and RabbitMQ have official JVM libraries but not Node.js ones. There is a third
    party Node.js library for RabbitMQ, but it lacks critical features such as publisher confirms.
  - The best relational DB library will be an SQL DSL. JVM has jOOQ but it's next to impossible to find such libraries
    in other ecosystems.
- It has the best developer tooling. For example:
  - IntelliJ IDEA for Kotlin.
  - Kotlin's coroutines support asynchronous programming, channels, reactive programming, etc.
  - Unlike build systems in other ecosystems (Rust, JavaScript, Python, etc.), Gradle support scripting (comments,
    custom functions which utilize the power of a full programming language, etc.), stress-free dependency management (
    defaults to locked dependency versions unlike npm which defaults to downloading incompatible versions of specified
    packages because of its caret syntax, no lock files to manage, etc.), plugins, and installs itself (granted that you
    have JVM installed, Gradle will install itself along with the programming languages and libraries before compiling
    and running your application - all in a single command).
- It has the best syntax. For example:
  - It's expressional.
  - It has a consistent and powerful collections interfaces.
  - It has excellent utility functions such as picking a random element from a list
  - It supports advanced functional programming concepts such as `associateWith()`.
  - It supports advanced OOP concepts such as sealed interfaces.
- It compiles faster than Java even though it has more features (Java is considered to compile at a decently fast speed)
  , and runs faster than Go (Go is considered to run at a decently fast speed).
- It's multiplatform. If you use Kotlin/JS, you can install a JavaScript library, and it'll automatically download the
  TypeScript type definitions package for you too. You can use it to build cross-platform mobile apps via Kotlin/Native.
  It supports JVM, ES, native, GraalVM, etc.
- It has the best standard library. There's builtin lazy loading. Every collection, whether it's an immutable set, or a
  linked list, is just as easy to use because of consistent and concise APIs which allow developers to use the best data
  structure rather than the one that's more ergonomic to use.

</details>

## Message Broker

[RocketMQ](https://rocketmq.apache.org/)

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

## VM

- Use HotSpot by default.
- Use [GraalVM](https://www.graalvm.org/) if you need a low memory footprint, and can't run a VM (e.g., for system
  software).

<details>
<summary>Reason</summary>

- OpenJ9 doesn't have as much support as HotSpot and GraalVM.
- OpenJ9 is significantly slower. Though it uses less memory, and starts up faster, it's only a small improvement.

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

## Build System

[Gradle](https://gradle.org/)

- Use the [Gradle Shadow Plugin](https://imperceptiblethoughts.com/shadow/) to create builds.

<details>
<summary>Reason</summary>

- Uses a (Kotlin) DSL rather XML like Maven.
- Has a plugin system.
- It's the easiest build system in the world. If the user has a JVM installed, then a Gradle app will automatically
  install the build tool (Gradle will install itself), the dependencies (programming languages, libraries, etc.),
  compile, and run the app in a single command.
- It supports several programming languages (Swift, JavaScript, etc.), and even multiple languages in the same project
  such as seamlessly using Java and Kotlin side-by-side.

</details>

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

[Redisson](https://redisson.org/)

<details>
<summary>Reason</summary>

- The other Redis libraries state that they're simpler but Redisson only requires one extra line of (copy-pastable)
  configuration (and that gives you the power of scaling to clusters of Redis instances). So, don't use the other
  libraries like Lettuce or Jedis; they only have a fraction of the features Redisson has.

</details>

## API

### Layer

If the API is for a client such as a frontend web app, or a microservice of a customer that queries your dataset,
use [GraphQL](https://graphql.org/).

<details>
<summary>Reason</summary>

- Larger APIs need GraphQL. Medium-sized APIs may eventually need GraphQL. So, it's better to start off with it because
  rewriting the entire API layer later on will take a very long time. Even smaller APIs should use GraphQL because the
  overhead of using it is worth the benefits of static typing (input validation, clients know how to deserialize
  responses because of the `__typename` field, etc.).

</details>

If the API only exists because a function happens to exist on another microservice, use [gRPC](https://grpc.io/).

<details>
<summary>Reason</summary>

- gRPC is essentially like calling a function that exists on another microservice. Its library makes it look like you're
  calling a local function. It uses a custom format (Protocol Buffers rather than JSON) to send messages between
  microservices for efficiency. It's not meant for querying data, or updating a DB like the typical API layer such as
  REST is meant for.
- It's the industry standard. For example, AWS lists gRPC as an option alongside HTTP when asking which type of
  networking you'll require.
- There's official support for every popular programming language.
- It's always getting improved, and companies like Netflix have dumped their own systems in favor of this.

</details>

If the API is for internal purposes such as a health check used by the cloud to know whether to restart your
microservice, or an admin API to reset a value stored in the DB, create a REST API.

<details>
<summary>Reason</summary>

- This is because there's a negligible amount of data getting transferred, that too only occasionally. This means that
  the overhead of setting up GraphQL and gRPC aren't worth it, and the efficiencies that they provide will never be
  realized.

</details>

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

[Vacuum](https://github.com/daveshanley/vacuum)

<details>
<summary>Reason</summary>

- [Spectral](https://stoplight.io/open-source/spectral) is the best linter because it's not opinionated, and works out
  of the box without any configuration. However, it's unusably slow. Vacuum is a drop-in replacement that uses
  Spectral's rules under the hood, and takes a negligible amount of time to execute.

</details>

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

### Relational DB Library

Relational DB library: [jOOQ](https://www.jooq.org/)

<details>
<summary>Reason</summary>

- ORMs generate slow code.
- ORMs require you to know not only SQL but their API as well.
- Since ORMs use custom APIs, most SQL features cannot be used which causes a mix of the ORM and raw SQL being used in
  the codebase which causes inconsistencies in style.

</details>

### Relational DB Migrations

[Liquibase](https://www.liquibase.org/)

<details>
<summary>Reason</summary>

- [Liquibase vs Flyway](https://www.baeldung.com/liquibase-vs-flyway)

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

## Web Framework

[Ktor](https://ktor.io/)

<details>
<summary>Reason</summary>

- Using frameworks such as Spring and Django is a bad idea because they attempt to do things that aren't related to web
  frameworks such as migrating database schemas. Such frameworks end up causing more code to be written (and worse code
  at that) to do pretty much anything.
- As this framework has been made by the same company that made Kotlin, it's ergonomic, and has a lot of support.

</details>

## JSON

[Jackson](https://github.com/FasterXML/jackson-module-kotlin)

<details>
<summary>Reason</summary>

- The other JSON libraries like Moshi and Gson seem to have better documentation, but they actually lack extremely basic
  functionality that only Jackson has.

</details>

## Encryption

[jasypt](http://www.jasypt.org/)

## Email

`com.sun.mail:javax.mail`

## Testing

[JUnit](https://junit.org/junit5/)

<details>
<summary>Reason</summary>

- It has a lot of support such as IDE plugins, and Gradle integrations since it's the industry standard.
- Easy to learn and use.

</details>
