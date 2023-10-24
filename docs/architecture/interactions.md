# Interactions

## Phases

The interactions among Nodes, Nodes and Supernodes, Supernodes and Catalogs, and all software components belonging to these objects, can be grouped in five phases:

### 1. Intent management

This phase is carried out by the [Service Handler](../main_activities/intentbased_computing_continuum/main_functional_elements/service-handler.md). It consists in the translation and the reduction to lowest terms of a received intent so that the [Node Orchestrator](../main_activities/intentbased_computing_continuum/main_functional_elements/node-orchestrator.md) can trigger the primitive functions of the Node to fulfill that intent.

### 2. Discovery

This phase consists in the discovery, both solicited or advertised, of flavours provided by other Nodes. It is mainly carried out by the [Discovery Manager](../main_activities/fluidos_node_implementation/main_functional_elements/discovery_manager.md) with the scope of filling the [Peering Candidates](../main_activities/fluidos_node_implementation/main_functional_elements/peering_candidates.md) table and provide suitable flavours to the [REAR Manager](../main_activities/fluidos_node_implementation/main_functional_elements/rear_manager.md). It relies on first couple of messages of the REAR protocol.

### 3. Reservation

This phase involves many components, since it consists in the contract signing step, managed by the [Contract Managers](../main_activities/fluidos_node_implementation/main_functional_elements/contract_manager.md) of both Nodes, and the actual resources reservation step, that consists in updating of the [Available Resources](../main_activities/fluidos_node_implementation/main_functional_elements/available_resources.md) tables. The phase is synchronously coordinated by the [REAR Managers](../main_activities/fluidos_node_implementation/main_functional_elements/rear_manager.md) of both Nodes.

### 4. Peering

The Peering phase is carried out by the [Virtual Fabric Managers](../main_activities/fluidos_node_implementation/main_functional_elements/virtual_fabric_manager.md) of both Nodes: it basically relies on the primitives provided by LIQO to establish the peering between the two nodes and extend the continuum, exploiting virtual routers created by the [Network Managers](../main_activities/fluidos_node_implementation/main_functional_elements/network_manager.md) to ensure node-to-node reachability.

### 5. Usage

This phase is managed by the [Node Orchestrator](../main_activities/intentbased_computing_continuum/main_functional_elements/node-orchestrator.md) of the Consumer Node and consists in the actual deployment of the workload on the Kubernetes Virtual Nodes created as output of the Peering phase, so that the real workload is automatically moved to the Provider Node for execution.

This is the phase where the two Telemetry Services are working actively to monitor both the [Local](../main_activities/fluidos_node_implementation/main_functional_elements/local_telemetry_service.md) and [Remote](../main_activities/fluidos_node_implementation/main_functional_elements/remote_telemetry_service.md) performances to populate the [Ratings and Metrics](../main_activities/fluidos_node_implementation/main_functional_elements/ratings_and_metrics.md) table.

### 6. Tear down

This is the phase where the process is unset, the peering is teared down, and the resources are freed and made available again for future processes. Its triggered by the [Node Orchestrator](../main_activities/intentbased_computing_continuum/main_functional_elements/node-orchestrator.md) and involves all the components that previously have cooperated to take the whole process up.


# IPC and protocols

The phases described make use of a set of inter-process communication methods and protocols.

## REAR

The **REAR** protocol enables different actors to perform actions on resources and services. This is a standardized method of communication for providers to advertise their resources. At the same time, potential clients can explore and identify the resources or services they need.
REAR defines a method through which resource management systems and platforms can be seamlessly integrated.

More information about this protocol can be found [here](https://github.com/fluidos-project/REAR).