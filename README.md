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
- Here's why you shouldn't use [Linear](https://linear.app/) (note that this is from a developer's perspective, and
  Linear might be fine if you're something like a designer):
  - Linear's roadmaps are useless because they can't contain issues - only projects. However, most issues don't fit into
    projects. On the other hand, GitHub's organization-level kanban boards will work for the roadmap use case.
  - Linear's projects are useless because:
    - There's no distinction between a project and a parent issue.
    - Projects aren't grouped. So, when an issue is to be added to a project, not only does a user have to go through
      countless projects to find which one to place the issue in, but it's not clear which project belongs to which
      roadmap/product.
  - Linear's issues are useless because:
    - If you have an open source GitHub repo, then users can't create issues in your Linear dashboard. Though there's a
      GitHub migration tool, it's useless enough that I had to manually move tens of issues into Linear instead.
    - Labels aren't confined to a particular GitHub repo. At first glance this looks more scalable as common labels
      don't need to be recreated on different repos, and it should make querying a label easier since they're
      consistent. However, in reality it has the opposite effect as people accidentally use incorrect labels, and most
      labels are clutter (which has the added disadvantage of people not labeling issues correctly thereby making it
      harder to query labels).
    - There's no way to figure out which repo an issue belongs to. Creating top-level labels for each repo to use for
      this case would cause too much clutter but creating a label group disallows multiple repos' labels from getting
      used.
    - Issues can have sub-issues but this causes all sorts of logistics problems. If a person is assigned a sub-issue,
      should they read the parent issue? What about other sub-issues? Which sub-issue should be completed first? It's
      common that a sub-issue will have a deadline that surpasses that of the parent issue which makes no sense. Due to
      the clutter caused by having sub-issues, people usually filter their views to only see parent issues but then they
      also have to remember to view sub-issues from time to time.
  - In GitHub, you can reference issues and PRs via a hash such as `#34`, and GitHub will automatically link to it.
    It'll also automatically close issues with relevant docs when a PR which states that it fixes those issues gets
    merged. Linear has no such functionality. Not only does GitHub not work with Linear but Linear's GitHub integration
    causes more issues than it solves. Linear allows you to get issue/PR IDs that will allow you to duplicate the
    aforementioned GitHub functionality but it doesn't actually work. For example, you won't get autocomplete in the
    GitHub editor when attempting to reference a Linear issue (obviously), the IDs are long and unreadable, and merging
    a PR closes the Linear issue even though many times you have multiple PRs that need to be merged before the Linear
    issue should get closed.
  - Some people use Linear to get an idea of what people are doing but GitHub gives a view of this as well. Simply go to
    the individual's profile, and you can see the tasks completed on the days they were actually completed (Linear has
    an issue where the date an issue was manually marked completed is used as the date it was actually completed unlike
    in GitHub where this usually happens automatically via PRs linking to issues). You can also use the filters in the
    search bar, or use GitHub's advanced search UI to filter what you want to see. It's possible that Linear is
    noticeably better than GitHub for your use case but from mine, GitHub is significantly better for this use case.
  - Linear has cycles which are like Agile sprints but GitHub can do the same thing using organization-level kanban
    boards. Simply have a kanban board for each individual (or a column for each individual in the same kanban board).
  - Linear doesn't have a proper review system. GitHub allows you to tag multiple reviewers who will only get notified
    once the PR is ready to be reviewed but Linear has no such feature (there's a review feature, but it causes more
    harm than good).
  - While I've rarely (if ever) faced a GitHub issues bug, I've faced multiple in Linear. For example, creating a
    roadmap takes you to an error page, and updating deadlines is difficult because the calendar is see-through. The
    most problematic is the editor which can neither perform basic tasks like updating a checklist nor is it intuitive
    enough to insert links with custom text.
  - Using Linear brings the issues of having yet another tool to manage such as:
    - Having another browser tab open which is especially problematic on mobile (Linear's mobile site doesn't even have
      all the features when creating an issue even though it's a super basic page).
    - You'll need to pay for another service.
    - You'll need to manage users' access to another service.
  - Information is even more disparate. Some of it will be on GitHub PR comments, some on Slack, some on Linear, etc.
  - Similar to how the GitHub integration causes more pain than good, the Slack integration is quite bad. People abuse
    it to create issues rather than writing a proper description which hurts the ability to query the issue from Linear,
    and the reader has to waste time going through an entire Slack thread (of mostly irrelevant comments) to figure out
    what the issue is even about.
  - Due to the way Linear works, you can't use it for personal use. So, you'll have to learn and use GitHub issues for
    personal projects, and Linear for work.
  - What about issues that aren't related to GitHub repos such as following up on a Telegram chat? Store random issues
    either in a GitHub repo meant just for such issues (this is quite common on GitHub, and has been recommended by
    issue system creators for years) or in your filesystem (Google Drive, Notion, etc.).

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
