# Integration roadmap

The work that crosses packages. Each package's own work stays in its own
roadmap. Started 2026-11-24 from
[the review of 2026-11-23](https://github.com/epistemer/example/blob/main/docs/neozp-review-2026-11-23.md)
and [the decisions](decisions.md) that answered it.

## Rules

- **A finding is done when Confab deletes its workaround**, not when a
  package releases a fix.
- **Integration runs continuously.** Confab's CI builds against tagged
  releases and, nightly, against every package's `main`.
- **Amendments are batched**: one minor release per package for a round of
  findings, not a release per finding.

## I1: close Confab's first iteration

| ✓ | Item | Done when |
|---|---|---|
| ☑ | Fixes within each package's terms (review §4.5, and F4 as a doc fix plus a clearer `handlers gen` error) | released (2026-11-24) |
| ☑ | The amendments epistemer accepted on 2026-11-24 (the package Decision items on the neozp project) | released: handlers v0.4.0, ui v0.5.0, models v0.5.1, cfgx v0.3.1, i18n v0.4.0, errors v0.2.0 |
| ☑ | `handlers/middleware` (D4) | released in handlers v0.4.0 |
| ☑ | The v1 lines in errors', auth's and genx's roadmaps say D2 | merged in each repository (2026-11-24) |
| ☑ | Confab deletes its workarounds: `scripts/stub`, `internal/pg`, `flash.go`, `Recover`, the `postCode` recover, `dataLabel`, the double permission grants, `confab.css`'s F23 rule | [epistemer/example#2](https://github.com/epistemer/example/pull/2) (2026-11-25): 29 findings closed; F6, F13 and F18 deferred by epistemer; F33–F35 new |

## I2: Confab iteration 2, consolidation

| ✓ | Item | Done when |
|---|---|---|
| ☐ | Confab's CI: genx check, vet, handlers vet, tests against Postgres | green on tags |
| ☐ | A nightly build of Confab against every package's `main` | green, or a finding filed |
| ☐ | One end-to-end browser test: sign in, create and publish an event, review a talk | in CI |
| ☐ | A detail page with tabs and an embedded table (a speaker and their talks) | its findings recorded |
| ☐ | ui catalogue stories for Confab's own components | in CI |
| ☐ | Check that two commands of one app (`seed`, `serve`) can share the bbolt file | answered |

## I3: Confab iteration 3, people

A speaker portal where a second population of users signs in and edits only
its own talks (resource scope); staff invited into groups; recovery;
passkeys; OpenID Connect against a local provider; TOTP; step-up before a
dangerous action (`auth.Within`); auth's `Recorder` behind an activity page;
partner API keys.

Done when every auth flow runs in Confab, and resource scope and API keys
have a real app asking for them (auth's interface §9, handlers' backlog
item 3).

## I4: Confab iteration 4, background work

A call for papers that closes at a date (a job), reminder emails from
templates (message delivery), and speaker photos on a second storage
backend (files).

Done when each runs on a neozp package, or that package's brief cites this
iteration's code as its need (D5).

## New packages (D5)

| Order | Package | Starts from | State |
|---|---|---|---|
| 1 | [messages](https://github.com/epistemer/messages) | Confab's outbox; auth's `Sender` | brief written and reviewed (2026-11-24); questions with epistemer |
| 2 | [files](https://github.com/epistemer/files) | Confab's `files.go`; ui's uploads, which store nothing | repository created (2026-11-24) |
| 3 | [jobs](https://github.com/epistemer/jobs) | I4's job; zp's scheduler as corroboration | repository created (2026-11-24) |

Each starts with a brief, then a locked interface, under the same terms as
the other packages.
