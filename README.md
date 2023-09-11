# elastic-eck

## Usage

### Deploy `kube-state-metrics`
```
kubectl apply -f 00-kube-state-metrics
```

### Deploy elastic crd and operator
```
kubectl apply -f 01-eck-init
```

### Create namespace **monitoring**
```
kubectl create namespace monitoring
```

### Deploy elastic stack

Elasticsearch, Kibana, Fleet server

```
kubectl apply -f 02-elastic-stack
```

### Deploy fleet server managed elastic agent

Set `FLEET_ENROLLMENT_TOKEN` at `02-elastic-stack/elastic-agent-managed/ea-managed-daemonset.yaml`
```
kubectl apply -f 02-elastic-stack/elastic-agent-managed
```

### Cluster name in EKS, GKE, AKS

Refer https://www.elastic.co/guide/en/fleet/current/running-on-eks-managed-by-fleet.html for more details

Add the below processor 
```
- add_fields:
    target: orchestrator.cluster
    fields:
      name: do-elastic
      url: https://do-elastic
```
