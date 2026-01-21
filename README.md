# Monitoring (kube-prometheus-stack)

Установка выполнялась через Helm chart `prometheus-community/kube-prometheus-stack`.

## Установка
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

kubectl create namespace monitoring

helm install mon prometheus-community/kube-prometheus-stack \
  -n monitoring \
  --set grafana.service.type=LoadBalancer \
  --set prometheus.service.type=ClusterIP \
  --set alertmanager.service.type=ClusterIP
