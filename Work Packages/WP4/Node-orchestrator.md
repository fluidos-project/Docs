# Node Orchestrator

<details>
<summary><i>D2.1 Definition</i><p></summary>

> The node orchestrator is the FLUIDOS module responsible for the orchestration of the service
requests, either on the local node, or offloading them to a remote FLUIDOS node, based on
the current snapshot of the available resources database. Additionally, it interacts with and
coordinates other components, mainly the resource acquisition manager, to trigger the
acquisition of new resources and the setup of the appropriate network and storage fabrics
enabling transparent execution continuum, in case already available ones are not sufficient to
satisfy the incoming request.

</details>

The node orchestrator is responsible for finding the best suitable place to allocate the policy/intent provided by the [Service Handler](/Work%20Packages/WP4/Service-handler.md) and performing the enforcement and the proactive reactions. The allocation is achieved using different orchestration algorithms such as ILP, Greedy, etc. If there are no resources avaible, then the Node Orchestrator triggers the [REAR Manager](/Work%20Packages/WP3/REAR-manager.md). When the Node Orchestrator has new resources, it performs the peering and the offloading of the service to the remote resources. Additionally, the Node Orchestrator can make reactive reactions when triggered by the [Local Telemetry Service](/Work%20Packages/WP3/Local-telemetry-service.md) or the [Privacy and Security Manager](/Work%20Packages/WP5/Privacy-and-security-manager.md) in case of a SSLA violation, overload, lack security, etc.