# hpct-cluster-bundle

Some juju bundles are provided to set up an HPC cluster.

# Overview of an HPC Cluster

Head Node - Suitable for logging into the cluster. From this node
all services should be able (user account, home filesystem, access
to queueing system, and possibly one or more data filesystems. Data
filesystems may not be accessible to avoid causing unwanted
performance hits.

LDAP Node - Provides identity management to all nodes. Account
management is performed on this node.

Slurm Node - Provides a queueing system, in this case Slurm.
Job scheduling and accounting are done on this node. Job
submissions and job control are mediated by the queueing
system software running here.

Compute Node - Where jobs actually run. Direct access
(e.g., ssh) is typically limited or prevented. Jobs are
allocated part or all of the node resources.

# Juju Setup

To set up juju on a local machine:

```
```

To monitoring what is running on the juju system:

```
juju status --watch 5s
```

To monitor the juju logging:

```
juju debug-log
```

# Set Up Cluster

To deploy a cluster:

```
juju deploy <bundle.yaml>
```

When a bundle deploys, multiple applications are installed and configured.
For each machine (may be virtual) that juju has set up and is controlling,
a "node" operator will be running it. Ideally, a "node" operator should
run on its own machine. However, if there are not enough resources, a
single machine will run multiple "node" operators.

# Bundles

## `hpct-cluster-bundle-micro.yaml`

Components:

* 1x head node
* 1x ldap node
* 1x slurm node
* 2x compute nodes

