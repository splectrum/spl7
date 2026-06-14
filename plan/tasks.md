# Tasks

Working task list. The durable home for in-flight and queued work — checked in
so it survives sessions and stays out of the always-on context window. Update
as work moves; the git log is the history.

Status: ⬜ pending · 🔄 in progress · ✅ done (drop when stale).

## In progress

- 🔄 **Mycelium POC on the swarm.** Three phases proven in
  `p2p-docker-dev/spl7-phase-{1,2,3}`. Next: instance drive visible
  to other nodes (phase 4).

## Done

- ✅ **spl7 setup.** Coordination repo, references, plan.
- ✅ **Master data view design.** Six-folder tree settled. Design doc at
  `plan/master-data-view.md`.
- ✅ **Tree on the swarm (phase 1).** Platform node seeds the master data
  view on Hyperdrive; joining node replicates sparsely. Browser UI.
- ✅ **XPath/URI navigation POC (phase 2).** Hyperdrive-fs adapter maps
  isomorphic-git onto Hyperdrive v11. Mycelium select/get/put/remove
  works on the replicated drive. Three visibility modes proven.
- ✅ **Instance fork (phase 3).** Joining node forks the platform's tree
  into its own writable Hyperdrive + git repo. Independent commit history.
  Install (platform) → instance (node) lifecycle proven.

## Queued

- ⬜ **Instance replication (phase 4).** Node's instance drive visible
  to other peers on the swarm.
- ⬜ **Swarm data view.** The `swarm/` folder populated with entries for
  each node — the swarm as a navigable tree.
