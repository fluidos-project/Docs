# Remote Telemetry Service

The Remote Telemetry Service exposes to each peered node the aggregated information concerning the guest workloads therein hosted feeding the [Ratings and Metrics](ratings_and_metrics.md) database of the node owner of the service, thus enabling for the monitoring of their execution, and the verification that negotiated SLAs are respected. In case of violate SLAs or poor performance the Local Telemetry Service can trigger the [Node Orchestrator](../../intentbased_computing_continuum/main_functional_elements/node-orchestrator.md) to react reactively to the problem.
