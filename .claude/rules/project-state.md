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

## Next up

1. Design the master data view tree structure (the template)
2. Mycelium POC: navigation + git operations on the P2P substrate
