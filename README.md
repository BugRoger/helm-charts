# SAP Converged Charts

This repository contains Helm charts required by SAP Converged Cloud. 

These Helm charts that describe a whole region. They are reused and
parameterized per region.

### Structure

The structure should be two charts deep. On the first level we expect charts
that logically group a set of applications. These charts correspond to
Kubernetes namespaces. For example:


```
.
└── automation
└── kube-system
└── monitoring
└── openstack
```

These logical meta-charts can contain sub-charts or reference charts from other
repositories using Helm dependencies. They should not contain a deeper
structure of charts.

```
.
└── automation
    └── charts
        ├── arc
        └── lyra
```

### Install/Update of a Chart/Release 

Per convention we use the name of the meta-chart as namespace and name of the
release. Values are pulled in from a secret repository.

```
helm upgrade monitoring monitoring --values ../secrets/staging/monitoring.yaml --install --namespace monitoring
```

## Reusable Charts

The subfolder `common` contains charts that are not specific to Converged
Cloud. They can be reused and referenced in other projects.





