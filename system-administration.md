# System Administration

- Use [this](https://github.com/leapwallet/cosmos-node-setup) guide if you're setting up a Cosmos blockchain node.

## Programming Language

`sh`

<details>
<summary>Reason</summary>

- `sh` is supported by all major OSes including Windows via WSL.
- There are different versions of `bash`, and you don't know which version an OS will have, if it even has `bash`.

</details>

## Firewall

If you're using a cloud, then use the built-in firewall system such as AWS Security Groups. If you're not using a
cloud (Hetzner Robot, etc.), then use `ufw`.

## Intrusion Detection Systems

Each of the following tools should be used:

- [Fail2ban](http://www.fail2ban.org/wiki/index.php/Main_Page)
- [Snort](https://www.snort.org/)
- [OSSEC](https://www.ossec.net/)

<details>
<summary>Reason</summary>

- They're free. Paid tools are hardly better but are difficult to use, and cost more than renting the server itself.

</details>

## Shell

[`fish`](https://fishshell.com/)

<details>
<summary>Reason</summary>

- Unlike `zsh` which requires you to install several plugins before it's usable, `fish` works out of the box. It also
  has a plugin system in case you want advanced customization though.
- The syntax highlighting allows you to figure out whether a command will work without executing it.
- It saves command line history similar to a browser so that you can cycle through commands you've previously entered
  based on what you've already entered.
- It's scripting language is easy to read and write because it has `switch`, etc.
- It has a single configuration file without any clutter.
- It's easy to create functions/aliases.
- It's mostly POSIX compliant. The parts which aren't POSIX compliant are obvious, and therefore not a problem. Syntax
  highlighting will help you find issues when pasting a command that doesn't work with `fish` (which doesn't happen
  often), there's a big community which means that it's easy to find `fish` equivalents of `bash`, etc. commands, and
  the productivity gained from the features `fish` has to offer outweigh the lack of 100% POSIX compliance.

</details>

## VCS

[GitHub](https://github.com/)

<details>
<summary>Reason</summary>

- GitHub has an issue tracking system, CI/CD pipelines, etc. which are better than competitors' such as GitLab and
  BitBucket in terms of UI/UX and stability.

</details>

## Changelog

[Keep a Changelog](https://github.com/olivierlacan/keep-a-changelog)

## Reverse Proxy

[Caddy](https://github.com/caddyserver/caddy)

<details>
<summary>Reason</summary>

- Automatic HTTPS.
- Easy to use.
- Well supported.

</details>

## Domains

[Google Domains](https://domains.google/)

<details>
<summary>Reason</summary>

- Good UI/UX.
- Affordable.
- Integrates with other services such as Google Sites.

</details>

## Metrics

[Prometheus](https://prometheus.io/)

- Use Prometheus tools but don't install Prometheus itself - use Grafana Agent to transport telemetry.
- Use it with every supported integration such as [Caddy](https://caddyserver.com/docs/metrics)
  , [containers](https://github.com/google/cadvisor), and [Linux](https://prometheus.io/docs/guides/node-exporter/).

## Containerization

### Orchestrator

[Kubernetes](https://kubernetes.io/)

### Containers

[Docker](https://www.docker.com/)

<details>
<summary>Reason</summary>

- It has the most support since it's the industry standard.

</details>

## OS

[Ubuntu](https://ubuntu.com/download/server)

- Use a non-root user with `sudo` priveleges rather than the root user because otherwise it's too easy to accidentally
  delete system files.
- Use [Unattended Upgrades](https://github.com/mvo5/unattended-upgrades) for automatic OS updates.

<details>
<summary>Reason</summary>

- RHEL sounds good because it has paid support, but you're not going to use it because manually setting up servers is
  outdated. On the rare occasion that you have to manually set up a server, you're not going to want paid support
  because it complicates things. Since RHEL (incorrectly) sounds good, Fedora and CentOS sound good because they're free
  versions of RHEL. Since RHEL itself is useless, Fedora and CentOS are useless too. Since most packages are in Debian
  format, and most support is for Ubuntu, Ubuntu is the best server OS. Ubuntu sounds bad because there's Canonical
  spyware, Amazon adware, and bad UIs (the terminal's theme, certain versions have an ugly desktop environment, etc.)
  but those don't exist on Ubuntu Server. Ubuntu's corporate backing causes the desktop edition to be a bad distro, but
  it's also what causes the server edition to be a good distro because there are LTS releases, support for upgrading
  between LTS releases, etc. The skills are also transferable because the best distro for desktop usage is Pop!_OS which
  is an Ubuntu fork. So, it's not like you'll have to learn Fedora for desktop (personal) usage, and Ubuntu for server
  usage.

</details>

## Infrastructure as Code

[Terraform](https://www.terraform.io/)

## Bare Metal Server

[Hetzner](https://hetzner.com/)

<details>
<summary>Reason</summary>

- Affordable.
- Many options.
- Trustworthy (many use it).
- Easy to use.

</details>

## Cloud

[GCP](https://cloud.google.com/)

<details>
<summary>Reason</summary>

- AWS has an outdated and buggy UI.
- GCP's tools (Google Maps, AI, etc.) are better than their AWS equivalents.
- The programmatic interfaces to interact with AWS such as the CLI are unusable because they're outdated, in beta,
  deprecated, etc.

</details>

## Performance Alerts

[Grafana OnCall](https://grafana.com/products/oncall/)

- Use phone calls for urgent alerts.
- Use Slack if you're in a team, and email otherwise for non-urgent alerts.

<details>
<summary>Reason</summary>

- Integrates with monitoring tools such as logs, traces, and metrics (Prometheus, etc.).
- Affordable (unlimited free phone call alerts, etc.).

</details>

## RabbitMQ

If the cloud provider doesn't support RabbitMQ (for example, AWS's RabbitMQ product doesn't support most plugins), then
use [Stackhero](https://stackhero.io) because it's the cheapest available.

## Cosmos Blockchain Node Monitoring

[PANIC](https://github.com/SimplyVC/panic)

<details>
<summary>Reason</summary>

- FOSS (self-hosted).
- Provides configurable alerts such as governance notifications, and block sync lag out of the box.
- Good docs.
- Good support (there's a Telegram group for help).
- Frequently updated.
- Can be used for non-Cosmos blockchain nodes as well (it's scalable).

</details>
