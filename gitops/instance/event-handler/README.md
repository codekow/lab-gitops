# Notes

## Quickstart

```sh
oc -n openshift-monitoring \
  exec -c prometheus prometheus-k8s-0 -- \
    curl -s 'http://localhost:9090/api/v1/alerts' | \
  jq -r '.data.alerts[] | select(.state == "firing" or .state == "pending") .labels.alertname' | sort -u
```
