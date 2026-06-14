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

## Mycelium POC on the swarm (2026-06-14)

Three phases proven in `p2p-docker-dev/spl7-phase-{1,2,3}`:

1. **Tree structure (phase 1)** — platform node seeds the six-folder master
   data view on Hyperdrive; joining node replicates sparsely. Browser UI
   with node switcher for testing.
2. **Mycelium on Hyperdrive (phase 2)** — Hyperdrive-fs adapter maps
   isomorphic-git's fs surface onto Hyperdrive v11. Mycelium's
   select/get/put/remove + git commit all work on the replicated drive.
   Three visibility modes (raw/data/metadata) proven on both nodes.
3. **Instance fork (phase 3)** — joining node forks the platform's tree
   into its own writable Hyperdrive with independent git history. The
   Hyperdrive IS the .git — git objects stored as drive entries.

Key architectural finding: Hyperdrive's sparse replication gives finer
sparsity than git natively offers. Even tree entries (the Hyperbee B-tree
index nodes) are fetched on demand — a node only downloads the index
entries for the paths it accesses.

## Next up

1. Instance replication (phase 4) — node's instance drive visible to
   other peers on the swarm
2. Swarm data view — the `swarm/` folder populated with node entries
