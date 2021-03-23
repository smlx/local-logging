Start a local kind cluster running `lagoon-logging` and `lagoon-logs-concentrator`, talking to an elasticsearch cluster running in docker-compose.

```
git clone git@github.com:uselagoon/lagoon-charts.git
git clone git@github.com:smlx/local-logging.git
cp local-logging/* lagoon-charts
cd lagoon-charts
make create-kind-cluster
docker-compose up -d
helm upgrade --install --create-namespace --namespace lagoon-logs-concentrator --wait --timeout 15m --values lagoon-logs-concentrator.values.yaml lagoon-logs-concentrator ./charts/lagoon-logs-concentrator
helm upgrade --install --create-namespace --namespace lagoon-logging           --wait --timeout 15m --values lagoon-logging.values.yaml lagoon-logging ./charts/lagoon-logging
```
