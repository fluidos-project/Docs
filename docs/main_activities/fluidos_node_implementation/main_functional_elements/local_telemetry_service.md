# Local Telemetry Service

<details>
<summary><i>D2.1 Definition</i><p></summary>

> The telemetry service is the FLUIDOS component responsible for the monitoring of the infrastructure (e.g., actual CPU load, memory, network, as well as possibly more detailed indexes such as memory page faults), including the collection of all the observability parameters key to enforce and verify the satisfaction of the workload requirements expressed through the intent-based API.

</details>

The Local Telemetry Service is responsible for the performance of the local FLUIDOS node, which is additionally leveraged by the [Local Resource Manager](local_resource_manager.md) to derive the locally available resources. The Local Telemetry Service is in charge of the monitoring of the infrastructure (e.g., actual CPU load, memory, network, etc) and the verification that negotiated SLAs are respected. The outcome of the monitoring process enriches the [Ratings and Metrics](ratings_and_metrics.md) database.. In case of violate SLAs or poor performance the Local Telemetry Service can trigger the [Node Orchestrator](../../intentbased_computing_continuum/main_functional_elements/node-orchestrator.md) to react reactively to the problem. 
