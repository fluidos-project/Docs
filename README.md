<p align="center">
<a href="https://www.fluidos.eu/"> <img src="./docs/images/fluidoslogo.png" width="250"/> </a>
<h1 align="center">FLUIDOS Official Documentation</h1>
</p>

This repository aims to be the single source of truth about the architecture and the behavior of the FLUIDOS ecosystem. It will also be an indexing point for all the artifacts and repositories involved.

This is not intended as a project deliverable, but as a guidance for FLUIDOS partners to address the several activities to be carried out throughout the development.

# Table of contents

- [What is FLUIDOS](#what-is-fluidos)
- [Architecture](#architecture)
  - [Objects](#objects)
  - [Data structures](#data-structures)
  - [Interactions](#interactions)
  - [Workflows](#workflows)
- [Main Activities](#main-activities)
- [License](#license)
---

# What is FLUIDOS

The IT landscape has evolved into a world of hyperconnectivity, where devices and information systems communicate and exchange data on numerous applications. FLUIDOS will leverage the enormous, unused processing capacity at the edge, scattered across heterogeneous edge devices that struggle to integrate with each other and to form a seamless computing continuum coherently.

# Architecture

FLUIDOS architecture is made up of two main objects, very different from each other still greatly coupled in several workflows: the **Node** and the **Catalog**. While the first is mandatory, as it's the base element of the ecosystem, the latter is optional, and jumps in whenever there's the need to go cross-domain or let the general public access the ecosystem through a user interface.

- ## [Objects](./docs/architecture/objects.md)
    - [Node](./docs/architecture/objects.md#node)
    - [Supernode](./docs/architecture/objects.md#supernode)
    - [Catalog](./docs/architecture/objects.md#catalogue)
- ## [Data structures](./docs/architecture/data_structures.md)
  - [Flavour](./docs/architecture/data_structures.md#flavour)
  - [Contract](./docs/architecture/data_structures.md#contract)
  - [Allocation](./docs/architecture/data_structures.md#allocation)
- ## [Interactions](./docs/architecture/interactions.md)
  - [Phases](./docs/architecture/interactions.md#phases)
      - [1. Intent management](./docs/architecture/interactions.md#1-intent-management)
      - [2. Discovery](./docs/architecture/interactions.md#2-discovery)
      - [3. Reservation](./docs/architecture/interactions.md#3-reservation)
      - [4. Peering](./docs/architecture/interactions.md#4-peering)
      - [5. Usage](./docs/architecture/interactions.md#5-usage)
      - [6. Tear down](./docs/architecture/interactions.md#6-tear-down)
  - [IPC and protocols](./docs/architecture/interactions.md#ipc-and-protocols)
      - [REAR](./docs/architecture/interactions.md#rear)

- ## Workflows

  Different type of workflow can be identified according to the presence of specific components in the scenario and the location of the involved nodes. The following workflows are described:

  1. Same domain scenario:
      1. [Two nodes](./docs/workflows/same_domains/two_nodes.md)
      1. [A node and the supernode](./docs/workflows/same_domains/node_supernode.md)
  2. Different domains scenario:
      1. [Two nodes](./docs/workflows/different_domains/two_nodes.md)
      2. [Two nodes with catalog](./docs/workflows/different_domains/two_nodes_catalog.md)

# Main Activities

  The FLUIDOS architecture is presented mostly in a technology-agnostic fashion. All technology-dependent and implementation related details are addressed in deliverables provided by the following main activities: 

  - [FLUIDOS Node Implementation](./docs/main_activities/fluidos_node_implementation/index.md)
    - [Main Functional elements](./docs/main_activities/fluidos_node_implementation/index.md#1-main-functional-elements)
    - [Relationships](./docs/main_activities/fluidos_node_implementation/index.md#2-relationships)
    - [Operation logic](./docs/main_activities/fluidos_node_implementation/index.md#3-operation-logic)
    - [Interfaces](./docs/main_activities/fluidos_node_implementation/index.md#4-interfaces)
    - [Abstraction & Models](./docs/main_activities/fluidos_node_implementation/index.md#5-abstraction--models)
    - [Ontology](./docs/main_activities/fluidos_node_implementation/index.md#6-ontology)
    - [Catalogue](./docs/main_activities/fluidos_node_implementation/index.md#7-catalogue)
    - [The Supernode](./docs/main_activities/fluidos_node_implementation/index.md#8-the-supernode)
    - [Tethered Mode](./docs/main_activities/fluidos_node_implementation/index.md#9-tethered-mode)
  - [Intent-based Computing Continuum](./docs/main_activities/intentbased_computing_continuum/index.md)
    - [Main Functional elements](./docs/main_activities/intentbased_computing_continuum/index.md#1-main-functional-elements)
    - [CLI extension](./docs/main_activities/intentbased_computing_continuum/index.md#bonus-cli-extension)
  - [Security](./docs/main_activities/security/index.md)
    - [Main Functional elements](./docs/main_activities/security/index.md#1-main-functional-elements)
  - [Energy and Cost-effective Infrastructure](./docs/main_activities/energy/index.md)

# License

The FLUIDOS project is under the Apache 2.0 license. Please [see details here](LICENSE).