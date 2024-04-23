# Step 12: Flavor Purchase - Provider side

&#8617; [Index](../../two_nodes.md)

![Step 12 flowchart](../../../images/workflows/steps/Workflow-12-FlavorPurchase(Provider).drawio.png)

The Gateway on the provider receives the request to purchase a flavor from the consumer, through the REAR protocol (1).

The Gateway drafts a **Contract** for the flavor purchase and stores it into the cluster (2).

---
The **Contract** is a Kubernetes Custom Resource (CR) that represents the agreement between the provider and the consumer. It contains the flavor details, the consumer's information (buyer), and the provider's information (seller).

---
This contract is returned to the consumer through the Gateway (3).

---
PREVIOUS STEP: [Step 11: Flavor Purchase - Consumer side](./11_flavor_purchase_consumer.md) | NEXT STEP: [Step 13: Peering Establishment - Consumer side](./13_peering_establishment_consumer.md)
