# spl7 Plan

## Arc

Build the native Mycelium on the P2P swarm. Take the design and the
proven primitives from spl6 and produce a working data fabric.

spl6's arc: migrate → explore → design → prove primitives compose.
spl7's arc: design the data view → build navigation and git → tool the
swarm with real Mycelium structure.

## The master data view

A swarm has a master data view: a tree structure that gives visibility
to everything in the cluster. Packages available to the swarm, runtime
folders for peer state and operational data, shared structure every
member sees.

The tree uses the URI naming scheme settled in spl6 — lowercase
alphanumeric segments, underscore for namespace mounts, files without
extension. The tree is designed, not ad-hoc.

## Three git repo levels

**Template.** The empty structure — tree layout, namespace nodes,
metadata mounts. Reusable across swarms. A git repository.

**Install.** A fork of the template, populated with installed
functionality for a specific swarm. Packages, apps, configuration. The
swarm's configured reality.

**Instance.** A fork of the install, created at swarm instantiation.
Each peer gets its own instance — own git repo, own Hyperdrive, own
identity. Single owner, single writer. The install is the upstream.

## Hyperdrive backed by git

Each peer's Hyperdrive (replication + FUSE surface) is backed by a git
repository. Hyperdrive provides P2P distribution; git provides
versioning, checkpointing, the transaction model. The git repo tracks
what the peer holds.

## Navigation and operations

**XPath/URI navigation** with the settled naming scheme. Pointer records
(fully resolved references). Selectors always return arrays. Opaque
bytes — no AVRO interpretation.

**Git operations** — simple: commit (checkpoint), push (propagate).
No merge — single writer, no conflict surface. Push latest.

## POC scope

The POC proves:

- The master data view as a designed Mycelium tree
- Template → install → instance lifecycle through git
- XPath/URI navigation (opaque bytes, pointer records, always-array)
- Git operations on P2P substrate (isomorphic-git on Hyperdrive)
- Hyperdrive-backed git as peer's data surface

**Not in scope:** AVRO (Round 2), Kafka topics, merge/conflict
resolution, upstream pull (install → instance updates), multi-writer.

## Beyond POC (carries forward)

- Mycelium design Round 2 — AVRO, schema-aware navigation, schema
  evolution
- Kafka topics — immutable data change event streams
- SPLectrum / HAICC pillar design review + documentation
- Infrastructure — private swarm, HiveRelay
- Pear documentation pages (splectrum.world)
- Doc-freshness agent routine
- Backlog: context stream types, CLI help rendering
