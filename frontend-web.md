# Frontend Web

- Here's a [template](https://github.com/neelkamath/js-lib-template) for a library.
- Here's [boilerplate](index.html) for an HTML file.

## Programming Language

[TypeScript](https://www.typescriptlang.org/)

Kotlin might be superior, but I'm not sure because I haven't tried Kotlin for frontend web.

<details>
<summary>Reason</summary>

- Flow doesn't have as much support.
- JavaScript isn't statically typed.

</details>

## Package Manager

[npm](https://www.npmjs.com/)

<details>
<summary>Reason</summary>

- Yarn is not supported nearly as much such as the docs to publish private npm packages.
- All of Yarn's features have been copied over to npm.
- Yarn requires more work (must be installed separately while npm is installed automatically with Node.js, etc.).

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

### Logs, Traces, and Metrics

[Faro](https://grafana.com/oss/faro/)

### Log Format

[The Syslog Protocol](https://datatracker.ietf.org/doc/html/rfc5424)

<details>
<summary>Reason</summary>

- It's the industry standard.

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

### Visual Testing

[Percy](https://percy.io/)

## Containerization

[Docker](https://www.docker.com/)

- Don't use containers in production as the app will be slow. Host the static files on a CDN instead.

<details>
<summary>Reason</summary>

- It has the most support since it's the industry standard.

</details>

## Illustrations

- [unDraw](https://undraw.co/)
- [Illustration Kit](https://illustrationkit.com/)
- [Multicolor illustrations](https://2.flexiple.com/scale/multi-color-illustrations)

## Favicon

[Generator](https://favicon.io/)

<details>
<summary>Reason</summary>

- Free.
- Easy to use.

</details>

## QR Codes

[qrcode.react](https://www.npmjs.com/package/qrcode.react)

## Design

[Design Resources](https://designresourc.es/)

## UI Library

[React](https://reactjs.org/)

<details>
<summary>Reason</summary>

- Templating languages such as those used in Vue and Svelte are bad because they require you to learn a new language,
  but they don't even have as much functionality as a programming language. React uses JavaScript to build the UI rather
  than a custom templating language.
- The best support in the ecosystem.

</details>

## Toasts

[React Hot Toast](https://react-hot-toast.com/)

## Big Numbers

[bignumber.js](https://www.npmjs.com/package/bignumber.js/v/9.0.1)

## State Management

[Jotai](https://jotai.org/)

<details>
<summary>Reason</summary>

- Redux is unnecessarily verbose.
- Recoil has a poorly written API. It's half like Redux which is what it was trying to replace.

</details>

## Markdown

[react-markdown](https://www.npmjs.com/package/react-markdown)

<details>
<summary>Reason</summary>

- It has plugins for GitHub flavored markdown, etc.

</details>

## Design Systems

Use one of:

- [antd](https://ant.design/)
- [GitHub Primer](https://primer.style/)
- [NextUI](https://nextui.org)

<details>
<summary>Reason</summary>

- Good UI/UX.
- Many components.

</details>

## UI Component Docs

[Storybook](https://storybook.js.org/)

## Tool Manager

[Volta](https://github.com/volta-cli/volta)

<details>
<summary>Reason</summary>

- Node Version Manager doesn't automatically switch to the right Node.js version.
- Node Version Manager is difficult to use (complicated installation instructions, doesn't work out of the box with fish shell, etc.).

</details>
