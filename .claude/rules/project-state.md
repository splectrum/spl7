# Project State

Snapshot of where the work stands. Update at commit points
when the state shifts. Reflects current reality, not history
— the git log is the history.

## Initialisation (2026-06-08)

spl7 created as coordination repo. Workspace repos:
`~/pear-full-square/mycelium` and `~/pear-full-square/hyperdrive-fuse`.
Previous repos (spl5, spl6) available as read-only references.

## What's settled (from spl6)

- Mycelium Round 1 design: git for mutable structure, Hypercore for
  immutable streams, XPath/URI navigation, opaque bytes
- URI naming scheme: `[_a-z0-9][a-z0-9]*`, no multiword separators,
  underscore as namespace mount, files without extension,
  packed/unpacked indifference
- XPath: pointer records, always-array return, future substrate-aware
  functions
- Git/Kafka authority split: git authoritative for structure, Kafka
  authoritative for data
- Swarm architecture: bridgehead container, FUSE Hyperdrive, two-tier
  execution, single-writer per peer
- P2P primitives: all proven under Bare (isomorphic-git, Hyperswarm,
  protomux, Hyperdrive, reactive dataflow)

## Master data view (2026-06-12)

Node tree structure designed — six top-level folders: `packages`,
`modules`, `components`, `config`, `home`, `swarm`. Design doc at
`plan/master-data-view.md`. This is the runtime layout for a swarm
node (container or host OS). The `swarm` folder carries the full
swarm data view. All nodes start from the same structure; POC platform
node populates, additional nodes get sparse copies.

## Next up

1. POC template instance — create the six-folder tree to work with
2. XPath/URI navigation POC on the template instance
3. Git operations POC (isomorphic-git on Hyperdrive)
