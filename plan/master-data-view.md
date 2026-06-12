# Master data view — tree structure design

The node tree structure. Each swarm node gets this tree as its root.
The tree includes the node's own folders and, under `swarm/`, the full
swarm data view. All nodes start from the same structure.

POC: a platform node is created first and populates the template.
Additional nodes start with a sparse copy — full structure, data
hydrated on access.

## The tree

Six top-level folders. This is the runtime layout for where a swarm
node executes (container or host OS).

```
/
  packages          available software (catalog)
  modules           installed software (active on this node)
  components        available components (catalog)
  config            runtime/execution config + node identity
  home              own space — component instances, host exchange
  swarm             full swarm data view
```

### packages

Software available to this swarm. Packages that can be activated on a
node. Available does not mean active — activation places software into
`modules`. Populated at swarm initiation.

### modules

Installed, active software on this node. Selected from `packages` and
ready to execute. Populated at swarm initiation.

### components

SPLectrum components available to this swarm. A component is a data
owner — a git repo with colocated functionality. This folder holds
the catalog; running instances live in `home`. Populated at swarm
initiation.

### config

Runtime/execution configuration. The boot process reads this to know
what to do — node identity, role, template provenance, wiring.
Populated at swarm initiation, tunable at runtime.

### home

The node's own space. Component instance repos (running data owners),
host exchange workspace. Populated at runtime. Internal structure for
later.

### swarm

The full swarm data view — everything in the swarm's data world. Each
node under the swarm has the same six-folder structure (self-similar).
Navigating into `swarm` can re-enter this node as a subfolder — the
circularity is structural and handled by pointer records and sparse
replication. Populated at runtime.

## To be POCed

- Reference format for external repos (`packages`, `components`)
- Software module format
- Component definition format

POC works with a template instance that evolves as these are built.

