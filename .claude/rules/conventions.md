# Working Conventions

How we collaborate on this repo. Update when a new
convention settles (comes up multiple times, or is
explicitly agreed).

## POC journey is kept; the installable graduates clean

While POCing, the full developmental journey is first-class and **committed** —
every step, iteration, probe and scratch. The value of a POC is the traceable
path: when something later changes or breaks, you can follow how it came to be.
When the package settles it becomes an **installable item** extracted from the
repo, and at that point it **sheds the historical journey**.

**Why:** During development, tracing *why* a thing is shaped the way it is (what
was tried, what failed, what the runtime actually does) is worth more than a
tidy tree. After it settles, the installable form shouldn't drag that history.

**How to apply:** Keep two layers. (1) *Developmental record* — `journey/`
(narrative + a committed full run log per phase) and `probes/` (re-runnable
de-risking setups, each with a committed `run.log`). Commit these. (2)
*Installable core* — the clean files that graduate. Only **generated** output
stays uncommitted (images, `node_modules`, ad-hoc capture logs); a representative
**run log is always committed** so any execution can be checked without re-running.
At graduation, extract the core and drop the journey.

## Task list lives in the repo

The working task list is `plan/tasks.md`, not the harness task tracker.

**Why:** The harness task list is injected into the context window on every
turn — it pollutes the view with standing state we don't need always-on. A
checked-in file is the durable home, survives sessions, and stays out of context
until consulted.

**How to apply:** Track in-flight and queued work in `plan/tasks.md`. Don't use
the harness Task tools for project tracking. (A short-lived harness checklist for
a single multi-step turn is fine, but clear it — don't let it persist.)

## Committed logs are scrubbed; cluster config is parameterised

Execution logs we commit (journey session samples, probe `run.log`s) are first run
through `scrub.sh` — it partially masks IPv4 addresses (keep network, mask host)
and long hex tokens (peer keys, topic hashes, container ids) **card-style**: front
starred, last 4 kept. The same value masks the same way every time, so logs stay
**correlatable within a run** without leaking full identifiers. Cluster config
(addresses / ports / topics) lives in `.env` (gitignored) with a committed
`.env.example`; nothing environment-specific is hardcoded in compose files.

**Why:** committed/public POC repos shouldn't carry environment specifics or
volatile identifiers — but we still want the execution logs as evidence of what
runs and works (the journey).

**How to apply:** never commit a raw log — pipe through `scrub.sh` (probe `run.sh`
already does). Keep config in `.env`; commit only `.env.example`.

## Commit pace

Work first, think through, iterate. Commit when a coherent
piece is done, not as a reflex after each change.

**Why:** Premature commits create noise and force review of
half-baked states. Design decisions are still forming during
implementation — commits should reflect settled pieces.

**How to apply:** Keep working, testing, iterating. Commit
when the user asks, or when a complete, tested, coherent
piece of work is ready.

## Doc prompts carry content, not site mechanics

Prompts we author for `the-world-of-splectrum` carry **content and
conceptual structure only**. Leave **all site mechanics to the executor** —
URLs, redirects / link preservation, navigation, sitemap, breadcrumbs,
frontmatter fields, and physical file/directory layout.

**Why:** Prescribing site mechanics derails the executor. Content/substance
is ours; repo specifics and voice are theirs.

**How to apply:** State *what* the page says and *how it's grouped*. Don't
state where files go, how URLs are preserved, or how nav/frontmatter is
updated. Make the prompt self-contained (no external references to
spl7-internal paths).

## Synthesise reference docs properly; an agent keeps them fresh

For the engineering reference docs, prefer **proper synthesised,
implementation-grade pages** — our orientation and structure + the gotchas +
enough to implement from. Accuracy against fast-moving upstream is held by a
**recurring freshness agent** that re-pulls each page's listed sources, diffs,
auto-fixes mechanical drift, and flags judgment calls.

**Why:** With an agent doing freshness, depth is maintainable and drift stops
being a reason to keep pages thin.

**How to apply:** every reference page carries a Sources block — that's the
anchor the agent re-checks. **Target reader: an AI agent consulting the page
to act** — give the real names/signatures, the gotchas, the relationships,
the sources, and honest uncertainty markers.

## Pressure-point approach

We deliberately defer some infrastructure investments until real pressure
surfaces. The risk is that under pressure we patch instead of invest.

**Why:** Premature abstraction against speculative needs ossifies shape badly.
But patches-under-pressure calcify worse.

**How to apply:** When pressure arrives on a deferred item, do the proper
investment, not a workaround. Track deferred items on the roadmap *with their
reason* so the reason can be re-evaluated later.

## Settled vision on paper, calibrated

Put settled vision on paper — but write only what has **settled**, at a
resolution that holds, and leave still-moving parts **explicitly open**
rather than prematurely pinned.

**Why:** The failure mode is *over-elaboration*: writing speculative detail
at a resolution that hasn't settled, which the next iteration contradicts.

**How to apply:** Decide what has settled before writing it. Mark open parts
open. Expect docs to be revised as iterations teach more — that's the method,
not drift.

## Distillation, not demolition

When reworking mature material, *extract and ground* the matured core —
don't rediscover it from scratch.

**Why:** Earned structure carries real settled thinking.

**How to apply:** Sort existing content into mature-core (keep/distil),
over-elaborated (trim to settled), and drifted/open (reconcile or mark open).

## Logical space vs implementation space

Think and discuss in the logical space. Build in the implementation space.
Don't blur the two.

**Why:** Jumping to code before the design is thought through produces work
that needs rethinking.

**How to apply:** When designing, discuss first. Don't rush to write documents
or code. When implementing, build.

## Aggressive simplification

Remove what we don't need. If the substrate provides a capability, don't
reimplement it. If something is optional, defer it. If it belongs to a
different concern, don't carry it.

**Why:** Complexity that doesn't earn its keep slows everything down. Every
layer should do its own job and nothing more.

**How to apply:** For every capability, ask: does the substrate already provide
this? Can it be deferred? Does it belong in this layer? Strip aggressively.

## Memory flow: session bank → repo

Session memory is scratch space for in-flight work. Once conventions or state
observations settle, transfer them into `.claude/rules/` (project-state.md for
state, this file for conventions) and commit. The memory bank remains useful
for the current session; the repo is the durable home.

**Why:** Memory that's about the project should follow the repo, not drift off
across sessions.

**How to apply:** During a session, write to the memory bank freely. At commit
points, sync what has bedded in to these files. Delete the transferred entries
so there's one source of truth.
