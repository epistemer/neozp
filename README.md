# neozp

The home of decisions that span more than one neozp package. neozp is a Go
framework built as eight separate libraries:

| Package | What it does |
|---|---|
| [cfgx](https://github.com/epistemer/cfgx) | schema-first configuration for cobra apps |
| [i18n](https://github.com/epistemer/i18n) | translations, which double as white-labelling |
| [genx](https://github.com/epistemer/genx) | the code generation driver |
| [models](https://github.com/epistemer/models) | labels, enums, listings and column sets over sqlc's models |
| [errors](https://github.com/epistemer/errors) | errors with a message for logs and one for people |
| [auth](https://github.com/epistemer/auth) | sign-in flows, sessions, devices, passkeys, OpenID Connect, permissions |
| [handlers](https://github.com/epistemer/handlers) | routes from comment directives and OpenAPI, with labels and permissions |
| [ui](https://github.com/epistemer/ui) | forms, tables, actions and components for Go and templ |

Each package keeps its own design, interface and roadmap in its repository.
This repository holds only what belongs to none of them alone:

- [docs/decisions.md](docs/decisions.md): neozp-wide decisions, dated.
- [docs/roadmap.md](docs/roadmap.md): the integration roadmap, the work
  that crosses packages.
- [docs/adr/](docs/adr/): neozp-wide ADRs.

The framework is checked by an app built on all eight packages,
[Confab](https://github.com/epistemer/example). Its
[findings](https://github.com/epistemer/example/blob/main/docs/findings.md)
are the evidence most decisions here rest on, and its
[review of 2026-11-23](https://github.com/epistemer/example/blob/main/docs/neozp-review-2026-11-23.md)
is the starting point of this repository.

Progress across sessions is tracked on the
[neozp project](https://github.com/users/epistemer/projects/3).
