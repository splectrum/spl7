# CLAUDE.md — Splectrum (spl7)

## What This Is

Splectrum is a framework at the intersection of
philosophy of language, systems theory, and software
engineering. Three fabrics: Mycelium (data fabric),
Splectrum (language fabric), HAICC (cognition fabric).

Philosophy drives engineering. The seed principles
(P0-P5) ground all design decisions.

## Documentation

splectrum.world is the public site for SPLectrum philosophy and
engineering work. Repo: `splectrum/the-world-of-splectrum`
(`~/splectrum/the-world-of-splectrum`); site files in `docs/`.

spl7 produces **prompt docs** for that repo to create/update
pages — it has its own editorial process, so we don't edit the
site pages directly from here.

Public documentation is a **core, ongoing workstream** — splectrum.world
aims to be a reference point for many, so structure and clarity carry
weight.

## Mission

spl7 builds the **native Mycelium on the P2P swarm**. spl6 proved
every primitive, designed the data layer (Round 1), and demonstrated
the swarm architecture. spl7 makes them work together as a real data
fabric.

**The deliverable:** a working swarm where each peer exposes a Mycelium
tree — navigable by URI/XPath, managed by git, backed by Hyperdrive —
instead of ad-hoc files. Opaque bytes (Round 1). Simple git operations.
Enough to tool the swarm for real.

**The approach:** three git repo levels (template → install → instance),
the master data view as a designed tree, Hyperdrive-backed git as the
peer's data surface. XPath/URI navigation with the naming scheme settled
in spl6. No AVRO (Round 2), no Kafka topics, no merge — POC scope.

The full plan is at `plan/README.md`.

## Repo Role

spl7 is the **coordination repo** — plans, designs, references, tasks,
documentation prompts. The actual workspace repos are:

- `~/pear-full-square/mycelium` — Mycelium POC workspace
- `~/pear-full-square/hyperdrive-fuse` — Docker/swarm workspace
- `~/splectrum/the-world-of-splectrum` — published documentation

Previous repos are **read-only references**:

- `~/splectrum/spl6` — design docs, POC catalogue, the TCP oracle
- `~/splectrum/spl5` — original fabric implementation

The reference index (`plan/references.md`) maps what lives where.

## How We Work

- **Entity:** Any participant. Human, AI, process.
- **Maximum beneficial autonomy:** If the system can
  do it, it should.
- **Technology decisions are AI's domain.** Decide.
- **Build, don't plan endlessly.** If wrong, fix it.
- **Philosophy first.** Engineering follows from the
  seed principles.
- **KISS.** Simplest mechanism that serves the purpose.
- **Engineering as conversation.** Natural language at
  the interaction level, rigid implementation beneath.
  Keep the human in the loop on direction.
- **Ask in prose.** Pose open questions in the
  conversation — no multiple-choice / option-picker
  questions.
- **Agree the approach before acting.** Discuss and
  confirm before starting any agent, background process,
  or outward/cross-repo action.
- **Don't keep old history.** Clean up spent or
  superseded working files rather than accumulating
  dead artifacts.

## Memory

This file (CLAUDE.md) is the single, in-repo memory —
kept lean. No out-of-repo memory bank. As it grows,
offload detail into other repo files (e.g.
`.claude/rules/`) and keep CLAUDE.md as the lean entry
point.

## Autonomy Target

Physical fully AI autonomous — structure, code,
environments, testing, deployment. Logical interactive
collaborative — scope, meaning, design, direction.
