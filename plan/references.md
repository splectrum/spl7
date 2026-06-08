# Reference Index

What lives where across repos. spl7 is the coordination repo;
previous repos are read-only references; workspace repos hold
the code.

## Workspace repos (`~/pear-full-square/`)

| Repo | Purpose |
|---|---|
| `mycelium/` | Mycelium POC workspace — navigation, git operations |
| `hyperdrive-fuse/` | Docker/swarm workspace — bridgehead, FUSE, containers |

## Design docs (`~/splectrum/spl6/plan/`)

| Document | What it covers |
|---|---|
| `mycelium-design.md` | Round 1 design — the elementary data building block |
| `p2p-building-blocks.md` | POC catalogue — every proven P2P primitive |
| `swarm-picture.md` | Swarm operating model — how the primitives compose |
| `swarm-app.md` | Swarm app plan and phase descriptions |
| `streaming-fabric.md` | Storage design — Hypercore/Hyperdrive mapping |
| `mycelium-streaming-layer.md` | Execution model — reactive dataflow |
| `spl7-preliminary.md` | The preliminary spl7 plan (written at spl6 close) |

## POC code (`~/splectrum/spl6/poc/`)

| Directory | What it proved |
|---|---|
| `p2p-docker-dev/phase-7-swarm-app/` | Swarm app — 7 phases, design.md |
| `p2p-docker-dev/` (earlier phases) | P2P primitives, probes, managed cluster |

## The oracle (`~/splectrum/spl6/`)

The spl5-carried fabric on TCP. 73 tests green. The correctness
reference for Mycelium behaviour. Key directories:

- `spl/` — namespace root (dispatch, xpath, git, process)
- `lib/` — dependencies (avsc, avsc-rpc, git, rpc-server)
- `_test/` — test framework and suites
- `_schema/` — schema registry

## Published documentation (`~/splectrum/the-world-of-splectrum/docs/`)

| Path | What it covers |
|---|---|
| `engineering/spl/platform/substrate/` | Language substrate — git, kafka, avro, uri, xpath |
| `engineering/spl/platform/swarm/` | P2P swarm and bridgehead |
| `engineering/spl/platform/` | SPL Platform landing page |
