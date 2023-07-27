# Docs

This repository aims to be the single source of truth about the architecture and the behavior of the FLUIDOS ecosystem. It will also be an indexing point for all the artifacts and repositories involved.

This is not inted as a project deliverable, but as a guidance for FLUDOS partners to address the several activities to be carried out throughout the development.

# Table of contents

- [Architecture](#architecture)
  - [Objects](#objects)
    - [Node](#node)
    - [Supernode](#supernode)
    - [Catalog](#catalogue)
  - [Data structures](#data-structures)
    - [Flavour](#flavour)
    - [Contract](#contract)
    - [Allocation](#allocation)
  - [Interactions](#interactions)
    - [Phases](#phases)
       - [1. Intent management](#1-intent-management)
       - [2. Discovery](#2-discovery)
       - [3. Reservation](#3-reservation)
       - [4. Peering](#4-peering)
       - [5. Usage](#5-usage)
       - [6. Tear down](#6-tear-down)
    - [IPC and protocols](#ipc-and-protocols)
       - [REAR](#rear)
  - [Workflows](./Workflows/README.md)
    - [1. Two nodes in the same domain](./Workflows/README.md#1-two-nodes-in-the-same-domain)
    - [2. A node and the supernode in the same domain](./Workflows/README.md#2-a-node-and-the-supernode-in-the-same-domain)
    - [3. Two nodes in different domains (w/o Catalog)](./Workflows/README.md#3-two-nodes-in-different-domains-wo-catalog)
    - [4. Two nodes in different domains (w/ Catalog)](./Workflows/README.md#4-two-nodes-in-different-domains-w-catalog)
- [Technical WPs](#technical-wps)
- [Links](#links)

---
# Architecture

FLUIDOS architecture is made up of two main objects, very different from eachother still greatly coupled in several workflows: the **Node** and the **Catalog**. While the first is mantatory, as it's the base element of the ecosystem, the latter is optional, and jumps in whenever there's the need to go cross-domain or let the general public access the ecosystem through a user interface.


## Objects


### Node

<details>
<summary><i>D2.1 Definition</i><p></summary>

> A FLUIDOS Node is a unique computing environment, under the control of a single administrative entity (although different Nodes can be under the control of different administrative entities), composed of one or more machines and modeled with a common, extensible set of primitives that hide the underlying details (e.g., the physical topology), while maintaining the possibility to export the most significant distinctive features (e.g., the availability of specific services; peculiar HW capabilities). <p>Overall, A FLUIDOS node is orchestrated by a single Kubernetes control plane, and it can be composed of either a single device or a set of devices (e.g., a datacenter). Device homogeneity is desired in order to simplify the management (physical servers can be considered all equals, since they feature a similar amount of hardware resources), but it is not requested within a FLUIDOS node. In other words, a FLUIDOS node corresponds to a Kubernetes cluster. <p>A FLUIDOS node includes a set of resources (e.g., computing, storage, networking, accelerators), software services (e.g., ready-to-go applications) that can be either leveraged locally or shared with other nodes. Furthermore, a FLUIDOS node features autonomous orchestration capabilities, i.e., (1) it accepts workload requests, (2) it runs the requested jobs on the administered resources (e.g., the participating servers), if application requirements and system security policies are satisfied, and (3) it features a homogeneous set of policies when interacting with other nodes.

</details>

A Node is a set of software components that live on a Kubernete cluster, whatever their kind (eg. Pod, DaemonSet, Service, Job etc.). Each Node embeds all the components, regardless of the role it takes on, while its behavior is role based. The components interact with eachother exploiting several transmission systems according to the number of interactions and the messages to be exchanged: as a rule of thumb, local interactions are mediated by Kubernetes Controllers, while external interactions are managed through RESTful APIs.

### Supernode

<details>
<summary><i>D2.1 Definition</i><p></summary>

> A FLUIDOS Supernode is a FLUIDOS node that acts as a “master” for an entire FLUIDOS domain, becoming the entity that can establish peering relationships on behalf of all nodes of a FLUIDOS domain toward a third-party Node, and acting as “aggregator” of resources and services for all the entire FLUIDOS Domain.

</details>

A Supernode acts as a *gateway* for domain's nodes that do not have access to the Internet or they don't know other domains. Its behavior is mostly similar to the node's one, with the main difference being the knowledge of other domains or catalogs with wich it can interact. The interactions exploit the same protocols and are managed by the same components, but the sources and destinations of the informations differ.

Besides acting as a gateway, a Supernode is another aggregation point in the distribution chain of informations. The specific tasks are deepened in the descriptive document of each component, while the interactions are shown in the workflows involving multiple domains.


#### Software components

The implementation of each component is responsibility of a single Work Package. The WPs assignements are highlighted inside the descriptive document of each component, and summerized in the per-WP index.

The Node/Supernode components are the following:

- [Service Handler](/Work%20Packages/WP4/Service-handler.md)
- [Node Orchestrator](/Work%20Packages/WP4/Node-orchestrator.md)
- [Local Resource Manager](/Work%20Packages/WP3/Local-resource-manager.md)
- [Local Telemetry Service](/Work%20Packages/WP3/Local-telemetry-service.md)
- [Remote Telemetry Service](/Work%20Packages/WP3/Remote-telemetry-service.md)
- [Ratings and Metrics](/Work%20Packages/WP3/Ratings-and-metrics.md)
- [Available Resources](/Work%20Packages/WP3/Available-resources.md)
- [REAR Manager](/Work%20Packages/WP3/REAR-manager.md)
- [Discovery Manager](/Work%20Packages/WP3/Discovery-manager.md)
- [Peering Candidates](/Work%20Packages/WP3/Peering-candidates.md)
- [Contract Manager](/Work%20Packages/WP3/Contract-manager.md)
- [Network Manager](/Work%20Packages/WP3/Network-manager.md)
- [Virtual Fabric Manager](/Work%20Packages/WP3/Virtual-fabric-manager.md)
- [Privacy and Security Manager](/Work%20Packages/WP5/Privacy-and-security-manager.md)
- [Trust and Security Agent](/Work%20Packages/WP5/Trust-and-security-agent.md)

### Catalog

<details>
<summary><i>Definition</i><p></summary>

> Lorem ipsum dolor sit amet

</details>

Lorem ipsum dolor sit amet

#### Software components

The Catalog components are the following:

- [Connector-UI](#)
- [Connector](#)
- [Broker](#)

## Data structures

### Flavour

<details>
<summary><i>Definition</i><p></summary>

> A FLUIDOS Flavour is the description of an available resources or services configuration.

</details>

Lorem ipsum dolor sit amet

### Contract

<details>
<summary><i>Definition</i><p></summary>

> Lorem ipsum dolor sit amet

</details>

Lorem ipsum dolor sit amet

### Allocation

<details>
<summary><i>Definition</i><p></summary>

> Lorem ipsum dolor sit amet

</details>

Lorem ipsum dolor sit amet

## Interactions

### Phases

The interactions among Nodes, Nodes and Supernodes, Supernodes and Catalogs, and all software components belonging to these objects, can be grouped in five phases:

#### 1. Intent management

This phase is carried out by the [Service Handler](/Work%20Packages/WP4/Service-handler.md). It consists in the translation and the reduction to lowest terms of a received intent so that the [Node Orchestrator](/Work%20Packages/WP4/Node-orchestrator.md) can trigger the primitive functions of the Node to fulfill that intent.

#### 2. Discovery

This phase consists in the discovery, both solicited or advertised, of flavours provided by other Nodes. It is mainly carried out by the [Discovery Manager](/Work%20Packages/WP3/Discovery-manager.md) with the scope of filling the [Peering Candidates](/Work%20Packages/WP3/Peering-candidates.md) table and provide suitable flavours to the [REAR Manager](/Work%20Packages/WP3/REAR-manager.md). It relies on first couple of messages of the REAR protocol.

#### 3. Reservation

This phase involves many components, since it consists in the contract signing step, managed by the [Contract Managers](/Work%20Packages/WP3/Contract-manager.md) of both Nodes, and the actual resources reservation step, that consists in updating of the [Available Resources](/Work%20Packages/WP3/Available-resources.md) tables. The phase is syncronously coordinated by the [REAR Managers](/Work%20Packages/WP3/REAR-manager.md) of both Nodes.

#### 4. Peering

The Peering phase is carried out by the [Virtual Fabric Managers](/Work%20Packages/WP3/Virtual-fabric-manager.md) of both Nodes: it basically relies on the primitives provided by LIQO to establish the peering between the two nodes and extend the continuum, exploiting virtual routers created by the [Network Managers](/Work%20Packages/WP3/Network-manager.md) to ensure node-to-node reachability.

#### 5. Usage

This phase is managed by the [Node Orchestrator](/Work%20Packages/WP4/Node-orchestrator.md) of the Consumer Node and consists in the actual deployment of the workload on the Kubernetes Virtual Nodes created as output of the Peering phase, so that the real workload is automatically moved to the Provider Node for execution.

This is the phase where the two Telemetry Services are working actively to monitor both the [Local](/Work%20Packages/WP3/Local-telemetry-service.md) and [Remote](/Work%20Packages/WP3/Remote-telemetry-service.md) performances to populate the [Ratings and Metrics](/Work%20Packages/WP3/Ratings-and-metrics.md) table.

#### 6. Tear down

This is the phase where the process is sunsetted, the peering is teared down, and the resources are freed and made available again for future processes. Its triggered by the [Node Orchestrator](/Work%20Packages/WP4/Node-orchestrator.md) and involves all the components that previously have cooperated to take the whole process up.


## IPC and protocols

The phases described make use of a set of inter-process communication methods and protocols.

### REAR

Lorem ipsum dolor sit amet


---

# Technical WPs

  - [Work Package 3](./Work%20Packages/WP3/README.md)
  - [Work Package 4](./Work%20Packages/WP4/README.md)
  - [Work Package 5](./Work%20Packages/WP5/README.md)
  - [Work Package 6](./Work%20Packages/WP6/README.md)

---

## Links

Lorem ipsum dolor sit amet


## License

The FLUIDOS project is under the Apache 2.0 license. Please [see details here](LICENSE).