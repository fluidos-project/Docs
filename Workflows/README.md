# Workflows

## 1. Two nodes in the same domain

![Workflow 1](./workflow_1.png)

1. A new _service request_ is sent to the **[Service Handler](../Work%20Packages/WP4/Service-handler.md)** in the form of an _intent_.
2. The _intent_ is passed to the **[Node Orchestrator](../Work%20Packages/WP4/Node-orchestrator.md)**, which translates and decomposes it to simple _resources or services requests_.
3. The **Node Orchestrator** looks up for _flavours_ matching the _request_ in the **[Available Resources](../Work%20Packages/WP3/Available-resources.md)** and the **[Ratings and Metrics](../Work%20Packages/WP3/Ratings-and-metrics.md)** tables.
4. In case there are no suitable available resources, the _request_ is passed to the **[REAR Manager](../Work%20Packages/WP3/REAR-manager.md)** to start-up the Discovery, Reservation and Peering phases.
5. The **REAR Manager** looks up in the **[Peering Candidates](../Work%20Packages/WP3/Peering-candidates.md)** table for potential peering candidates (suitable _flavours_) matching the _request_.
6. In case there are no suitable peering candidates, the the **REAR Manager** builds a _flavour selector_ and passes it to the **[Discovery Manager](../Work%20Packages/WP3/Discovery-manager.md)** asking for a suitable peering candidate.
7. The **Discovery Manager** of the Consumer Node sends a _LIST_FLAVOURS_ message to all the endpoints it already knows, whatever they are local Nodes, a Supernode or a Catalog.
8. The **Discovery Manager** of the Provider Node looks-up for suitable local _flavours_ matching the received _flavour selector_ in its **Available Resources** table.
9. In case one or more suitable _flavours_ are found, the **Discovery Manger** of the Provider Node sends back an OK message to the **Discovery Manager** of the Consumer Node attaching the _flavours_ list.
10. The **Discovery Manager** of the Consumer Node populates the **Peering Candidates** table with the newly discovered _flavours_.
11. It then informs the **REAR Manager** that the Discovery phase has completed successfully.
12. See <u>step #5</u>.
13. Now that a suitable peering candidate is found, the **REAR Manager** asks the **[Contract Manager](../Work%20Packages/WP3/Contract-manager.md)** to start-up the Reservation phase poiting to the Provider Node.
14. The **Contract Manager** of the Consumer Node sends a _RESERVE_FLAVOUR_ message to the **Contract Manager** of the Provider Node.
15. The **Contract Manager** of the Provider Node asks its **REAR Manager** to reserve resources for the incoming request.
16. The **REAR Manager** updates the **Available Resources** table by deleting the old advertised _flavour_ and creating a new reduced _flavour_ (suitable for other future requests) and by creating a new _allocation_ of type "Node" in "inactive" status.
17. The **REAR Manager** informs the **Contract Manager** that the resources have been reserved.
18. The **Contract Manager** of the Provider Node creates a new _contract_ and answers back to the **Contract Manager** of the Consumer Node with an _OK_ message.

Following the steps defined into the REAR Protocol, the two **Contract Managers** may exchange a couple of other messages to confirm the reservation on both sides, but may also directly agree following the procedure described from <u>step #14</u> to <u>step #18</u>.

19. The **Contract Manager** of the Consumer Node creates a new _contract_ and informs its REAR Manager that the resources have been reserved.
20. The **REAR Manager** updates the **Available Resources** table by creating a new _allocation_ of type "VirtualNode" in "inactive" status.
21. The **REAR Manager** asks the **[Resource Importer](../Work%20Packages/WP3/Resource-importer.md)** to start-up the Peering phase.
22. The **Resource Importer** of the Consumer Node sends a ResourceRequest to the **[Resource Exporter](../Work%20Packages/WP3/Resource-exporter.md)** of the Provider Node to trigger a LIQO Peering set-up.
23. The **Resource Exporter** of the Provider Node solicitates its **[Virtual Fabric Manager](../Work%20Packages/WP3/Virtual-fabric-manager.md)** (LIQO) to set things up.
24. Once done, an informer makes the **REAR Manager** aware.
25. The **REAR Manager** updates the **Available Resources** table by putting the previously created _allocation_ to "active" state.
26. At the same time, an informer makes the **Resource Exporter** aware.
27. The **Resource Exporter** of the Provider Node answers back the **Resource Importer** of the Consumer Node with a ResourceOffer.
28. The **Resource Importer** of the Consumer Node solicitates its **Virtual Fabric Manager** (LIQO) to set things up.
29. See <u>step #24</u>.
30. See <u>step #25</u>.
31. The **REAR Manager** finally informs the **Node Orchestrator** that all the Discovery, Reservation and Peering phases are over.
32. The **Node Orchestrator** is auto-solicitated to continue with the Intent Management phase.
33. See <u>step #3</u>

Now that there are available resources that fulfill the request, the **Node Orchestrator** can finally deploy the workload described in the _intent_ exploiting standard Kubernetes primitives and pointing to the VirtualNode retreived in the **Available Resources** table.

## 2. A node and the supernode in the same domain

Lorem ipsum dolor sit amet

## 3. Two nodes in different domains (w/o Catalog)

![Workflow 2](./workflow_3.png)

## 4. Two nodes in different domains (w/ Catalog)

Lorem ipsum dolor sit amet