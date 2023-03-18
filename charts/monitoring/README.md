Best Pratices in Monitoring a Kubernetes Cluster 

## Install kube-prometheus-stack
### Create a monitoring namespace 
+ `kubectl create namespace monitoring`

### Add prometheus-community repo
- `helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`
- `helm repo update prometheus-community`

### Use helm to install the kube-prometheus-stack
- `helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack -n monitoring` 


## Poke around prom, alertmanager grafana and alertmanager
Prometheus and Alertmanager Web Panel

+ `kubectl port-forward svc/kube-prometheus-stack-prometheus 9090:9090 -n monitoring` 

+ `kubectl port-forward alertmanager-kube-prometheus-stack-alertmanager-0 9093 -n monitoring`

Grafana Web Panel 

+ `kubectl port-forward svc/kube-prometheus-stack-grafana 3000:80 -n monitoring`

## Deploy Grafana Loki (values.yaml -> go to the gist for infos)

+ `helm install loki --namespace=monitoring -f values.yaml grafana/loki-stack`

## Poke around prom, alertmanager grafana and alertmanager with ingresses

[alertmanager](http://alertmanager.stage-1-eks-stage-ecom.altex.ro)

[grafana](http://grafana.stage-1-eks-stage-ecom.altex.ro)

[prometheus](http://prometheus.stage-1-eks-stage-ecom.altex.ro)
