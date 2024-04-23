# Step 10: Flavor Reservation - Provider side

&#8617; [Index](../../two_nodes.md)

![Step 10 flowchart](../../../images/workflows/steps/Workflow-10-FlavorReservation(Provider).drawio.png)

The provider FLUIDOS Node receives the request to reserve the specific Flavor through the Gateway and the REAR protocol (1).

The Gateway *reserves* the Flavor from the Available Resources setting an "Available" flag on the FlavorCR to `false` (2).

At the end of the process, the Gateway sends a response to the consumer with the confirmation of the reservation, which is limited in time (3).

---
PREVIOUS STEP: [Step 9: Flavor Reservation - Consumer side](./08_flavor_retrieve_consumer.md) | NEXT STEP: [Step 11: Flavor Purchase - Consumer side](./11_flavor_purchase_consumer.md)
