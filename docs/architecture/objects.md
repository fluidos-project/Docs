# Objects

## Node

<details>
<summary><i>D2.1 Definition</i><p></summary>

> A FLUIDOS Node is a unique computing environment, under the control of a single administrative entity (although different Nodes can be under the control of different administrative entities), composed of one or more machines and modeled with a common, extensible set of primitives that hide the underlying details (e.g., the physical topology), while maintaining the possibility to export the most significant distinctive features (e.g., the availability of specific services; peculiar HW capabilities). <p>Overall, A FLUIDOS node is orchestrated by a single Kubernetes control plane, and it can be composed of either a single device or a set of devices (e.g., a datacenter). Device homogeneity is desired in order to simplify the management (physical servers can be considered all equals, since they feature a similar amount of hardware resources), but it is not requested within a FLUIDOS node. In other words, a FLUIDOS node corresponds to a Kubernetes cluster. <p>A FLUIDOS node includes a set of resources (e.g., computing, storage, networking, accelerators), software services (e.g., ready-to-go applications) that can be either leveraged locally or shared with other nodes. Furthermore, a FLUIDOS node features autonomous orchestration capabilities, i.e., (1) it accepts workload requests, (2) it runs the requested jobs on the administered resources (e.g., the participating servers), if application requirements and system security policies are satisfied, and (3) it features a homogeneous set of policies when interacting with other nodes.

</details>

A Node is a set of software components that live on a Kubernetes cluster, whatever their kind (eg. Pod, DaemonSet, Service, Job etc.). Each Node embeds all the components, regardless of the role it takes on, while its behavior is role based. The components interact with each other exploiting several transmission systems according to the number of interactions and the messages to be exchanged: as a rule of thumb, local interactions are mediated by Kubernetes Controllers, while external interactions are managed through RESTful APIs.

## Supernode

<details>
<summary><i>D2.1 Definition</i><p></summary>

> A FLUIDOS Supernode is a FLUIDOS node that acts as a “master” for an entire FLUIDOS domain, becoming the entity that can establish peering relationships on behalf of all nodes of a FLUIDOS domain toward a third-party Node, and acting as “aggregator” of resources and services for all the entire FLUIDOS Domain.

</details>

A Supernode acts as a *gateway* for domain's nodes that do not have access to the Internet or they don't know other domains. Its behavior is mostly similar to the node's one, with the main difference being the knowledge of other domains or catalogs with which it can interact. The interactions exploit the same protocols and are managed by the same components, but the sources and destinations of the information differ.

Besides acting as a gateway, a Supernode is another aggregation point in the distribution chain of information. The specific tasks are deepened in the descriptive document of each component, while the interactions are shown in the workflows involving multiple domains.


### Software components

The implementation of each component is responsibility of a single Work Package. The WPs assignments are highlighted inside the descriptive document of each component, and summarized in the per-WP index.

The Node/Supernode components are the following:

- [Service Handler](../main_activities/intentbased_computing_continuum/main_functional_elements/service-handler.md)
- [Node Orchestrator](../main_activities/intentbased_computing_continuum/main_functional_elements/node-orchestrator.md)
- [Local Resource Manager](../main_activities/fluidos_node_implementation/main_functional_elements/local_resource_manager.md)
- [Local Telemetry Service](../main_activities/fluidos_node_implementation/main_functional_elements/local_telemetry_service.md)
- [Remote Telemetry Service](../main_activities/fluidos_node_implementation/main_functional_elements/remote_telemetry_service.md)
- [Ratings and Metrics](../main_activities/fluidos_node_implementation/main_functional_elements/ratings_and_metrics.md)
- [Available Resources](../main_activities/fluidos_node_implementation/main_functional_elements/available_resources.md)
- [REAR Manager](../main_activities/fluidos_node_implementation/main_functional_elements/rear_manager.md)
- [Discovery Manager](../main_activities/fluidos_node_implementation/main_functional_elements/discovery_manager.md)
- [Peering Candidates](../main_activities/fluidos_node_implementation/main_functional_elements/peering_candidates.md)
- [Contract Manager](../main_activities/fluidos_node_implementation/main_functional_elements/contract_manager.md)
- [Network Manager](../main_activities/fluidos_node_implementation/main_functional_elements/network_manager.md)
- [Virtual Fabric Manager](../main_activities/fluidos_node_implementation/main_functional_elements/virtual_fabric_manager.md)
- [Privacy and Security Manager](../main_activities/security/main_functional_elements/privacy_and_security_manager.md)
- [Trust and Security Agent](../main_activities/security/main_functional_elements/trust_and_security_agent.md)

## Catalog

<details>
<summary><i>Definition</i><p></summary>

> A FLUIDOS Catalog is a centralized repository that collects, manages, and shares peering credentials and commercial offers from provider clusters in a cloud environment, serving as a resource and service aggregator for the entire FLUIDOS Domain.

</details>

A FLUIDOS Catalog functions as a central hub within the FLUIDOS Domain, serving as a nexus for nodes that may lack direct access to specific information or other catalogs. Its behavior closely aligns with that of regular nodes but with a distinct focus on catalog-related knowledge and interactions. These interactions employ the same protocols and are managed by shared components, albeit with variations in the sources and destinations of the information.

In addition to its role as a knowledge hub, the FLUIDOS Catalog also acts as a pivotal point in the distribution of information across the FLUIDOS Domain. Specific tasks and functions are detailed in component-specific documents, while inter-domain interactions are elucidated within workflows involving multiple catalogs.

### Software components

The Catalog components are the following:

- [Connector-UI](#)
- [Connector](#)
- [Broker](#)