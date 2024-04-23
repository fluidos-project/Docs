# Step 7: Flavor Retrieve - Provider side

&#8617; [Index](../../two_nodes.md)

&#8617; [Index](../../two_nodes.md)

![Step 7 flowchart](../../../images/workflows/steps/Workflow-07-FlavorsRetrieving(Provider).drawio.png)

The remotes FLUIDOS Nodes will receive the request for listing flavors through the REAR Protocol. These FLUIDOS Nodes are providers.

The request is received by the **Gateway** (1). It acts as a *REAR server*, receiving a REAR request.

The Gateway determines which flavors are available and suitable looking at the Available Resources in the cluster (2). This dataset was previously populated ([Step 1 - Resource Discovery and Creation](./01_resource_detection.md)).

The set of flavors suitable to the previous request is sent back to the consumer through the Gateway (3).

---
PREVIOUS STEP: [Step 6: Discovery](./06_discovery.md) | NEXT STEP: [Step 8: Flavor retrieve - Consumer side](./08_flavor_retrieve_consumer.md)
