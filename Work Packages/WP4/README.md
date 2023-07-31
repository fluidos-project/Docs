# Work Package 4

# Introduction

Lorem ipsum dolor sit amet



# Activities

Lorem ipsum dolor sit amet

## 1. Main Functional elements

<p align="center">
<img src="./general_architecture.png" height="600">
</p>

- [Service Handler](./Service-handler.md)
- [Node Orchestrator](./Node-orchestrator.md)
- [Ratings and Metrics](/Work%20Packages/WP3/Ratings-and-metrics.md)

## Bonus: CLI extension
CLI extension implemented as a *kubectl* plugin:
```console
kubectl fluidos –f <FILE_PATH>
```

CLI:
* Inherits kubectl apply options, falls back to it for dummy behavior
* Inspects intent format to identify best matching service handler

No syntactic checks beyond validity of the serialization language performed.
Semantic validation of the request to be performed in the Service Handler.

*To be released at* https://github.com/orgs/fluidos-project/kubectl-fluidos-plugin






