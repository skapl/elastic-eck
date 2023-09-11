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
