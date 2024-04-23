# Step 8: Flavor Retrieve - Consumer side

&#8617; [Index](../../two_nodes.md)

![Step 8 flowchart](../../../images/workflows/steps/Workflow-08-FlavorsRetrieving(Consumer).drawio.png)

The consumer FLUIDOS Node receives the list of flavors suitable for the request it previously made. The list is received through the Gateway (1).

The Gateway will store each flavor as a **PeeringCandidate** CR in the cluster (2).

---
The **PeeringCandidate** is a Kubernetes Custom Resource (CR) that contains the information about a Flavor and its FLUIDOS Node provider. This CR is directly stored in the cluster.

---
This step of storing the PeeringCandidate is done for each remote FLUIDOS Node contacted. Once all of them responded, the *discovery phase* is set "solved".

---
PREVIOUS STEP: [Step 7: Flavor Retrieve - Provider side](./07_flavor_retrieve_provider.md) | NEXT STEP: [Step 9: Flavor reservation - Consumer side](./09_flavor_reservation_consumer.md)
