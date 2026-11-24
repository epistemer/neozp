# neozp-wide decisions

Decisions that bind more than one package, newest first. Each says who
decided, when, and what it rests on. A package's own decisions stay in its
repository.

## 2026-11-24: answers to the review of 2026-11-23

Decided by epistemer. The questions and their evidence are in
[the review](https://github.com/epistemer/example/blob/main/docs/neozp-review-2026-11-23.md)
(section 6.4). The answers that bind a single package are recorded on that
package's Decision item on the neozp project. The ones below bind several.

### D1. A home for seams (Q1)

This repository holds neozp-wide ADRs, decisions and the integration
roadmap. Confab ([epistemer/example](https://github.com/epistemer/example))
stays the example app and the cross-package check.

### D2. The v1 gate (Q2)

A package's `v1.0.0` waits until Confab uses its whole surface with no
open bug or contradiction finding against it. This is one rule for all eight
packages. It replaces the lines in errors', auth's and genx's roadmaps that
waited for zp to move, which the rule of 2026-11-16 had already overturned.
It also makes cfgx's and genx's "a real app" concrete. Tagging `v1.0.0`
stays epistemer's call.

### D3. Single process until v1 (Q3)

auth, i18n and cfgx's store keep their state in bbolt, so a neozp app is one
process until `v1.0.0`. The shared-store items in cfgx's and i18n's backlogs
stay parked.

### D4. handlers owns the request's lifecycle (Q4, Q6, H2)

A handlers subpackage, `handlers/middleware`, owns:

- panic recovery, used by default by generated `Register` and `Mount`;
- a flash: a level and an i18n key carried across a redirect, rendered in
  the reader's language;
- the redirect, htmx-aware redirect and error-page helpers;
- later, request ids and access logs.

ui only shows flashes as toasts, through an interface ui declares, so ui
keeps not depending on handlers. ui's `Reply` keeps its in-place updates
and hands its toast to the flash whenever it redirects.

This follows zp, whose admin handler and flash helpers are transport, not
presentation.

### D5. New packages: messages, then files, then jobs (Q5)

1. Message delivery comes first, because an app can't sign anyone in for
   real without it.
2. File storage comes second.
3. Jobs come third. Their brief waits until Confab has a real job.

Each brief starts from what Confab hand-wrote, with zp's code as
corroboration.

### D6. Permissions may be shared across routes packages (H3)

A route may name a permission that another routes package of the same app
declares. Declaring it twice stays an error. The admin and the API then
share one grant.

### D7. Enum values' English text is the value made readable (M5)

`in_review` becomes "In Review", as route keys are made readable. This
changes neozp's labels convention, under which an enum value's English
text was the value itself.

### Deferred

- **Searching routes that have parameters** (H5). epistemer has an idea of
  a parameter form, to discuss before handlers' search hits or ui's
  command palette change.
- **Forking htmx v2** (H6, U2), raised by epistemer. It holds handlers'
  method override for no-script actions and ui serving htmx.

## 2026-11-16: moving zp is out of scope

Decided by epistemer. Moving zp onto neozp is out of neozp's scope. No
package's roadmap plans, measures or waits for it, and no release
(`v1.0.0` included) is gated on it. zp's code is read only as a record of
what the framework must do.

## 2026-11-13: one generation pipeline

[neozp ADR 0001](https://github.com/epistemer/genx/blob/main/docs/adr/0001-generation-pipeline.md),
in genx: generators share metadata through domain files, which genx
orders. Code generators publish their labels as `labels/v1` data.
