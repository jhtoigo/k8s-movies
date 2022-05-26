
# Estudo do K8s

Este projeto é um estudo do K8s aplicando o conhecimento adquirido durante as aulas da Formação Kubedev.

Ao atualizar este repositório é executado uma pipeline CI/CD que cria uma nova imagem docker a partir do Dockerfile em src/Dockerfile e a salva com uma nova tag no DockerHub, em caso de sucesso do build e registro da nova tag é disparado o processo de deploy no K8s.

## Configurações para aplicação conectar no MongoDB

MONGODB_DB => Nome do database

MONGODB_HOST => Host do MongoDB

MONGODB_PORT => Posta de acesso ao MongoDB

MONGODB_USERNAME => Usuário do MongoDB

MONGODB_PASSWORD => Senha do MongoDB


# Instalação do Nginx Ingress Controller

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.2.0/deploy/static/provider/do/deploy.yaml
```

# Instalação do Prometheus no K8s

## Para instalar o Prometheus foi utilzado o Helm

Adicionado o repositório do Prometheus

Alterado o "scrape_interval: " para 15s no arquivo de values.

E instalado no namespace monitoramento.

```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm show values prometheus-community/prometheus > helm/prometheus-values.yaml
helm install prometheus prometheus-community/prometheus --values helm/prometheus-values.yaml --namespace monitoramento --create-namespace
```

# Instalação do Grafana no K8s

Adicionado o repositorio do grafana.

Instalado no namespace monitoramento.

```
helm repo add grafana https://grafana.github.io/helm-charts
helm install grafana grafana/grafana --namespace monitoramento
```


