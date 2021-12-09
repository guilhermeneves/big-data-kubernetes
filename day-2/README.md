# Big Data Infrastructure Backbone System

https://bitbucket.org/owshq/big-data-kubernetes/src/master/

## Kafka

KSQL le dados em realtime kafka utilizando sql.
Kafka Connect para migrar dados do SQL Server para Postgresql em tempo real por exemplo

## Environment

#  microsoft azure
# https://docs.microsoft.com/en-us/cli/azure/install-azure-cli
az account set --subscription []
az aks get-credentials --resource-group k8s-aks-owshq-dev --name aks-owshq-dev

# google gcp
# https://cloud.google.com/sdk/gcloud
gcloud container clusters get-credentials [] --region us-central1

# digital ocean
# https://docs.digitalocean.com/reference/doctl/how-to/install/
doctl kubernetes cluster kubeconfig save []

# linode
# https://www.linode.com/docs/guides/linode-cli/
cluster_id=[]
linode-cli lke clusters-list
linode-cli lke kubeconfig-view $cluster_id

# local kube config
```
kubectl config view
$HOME/.kube/config
```

## Some OpenSource

- ArgoCD (CI/CD)
- Yugabyte (ACID Distributed - POstgres e Cassandra)
- Clickhouse & Pinot & Druid (OLAP) ** Melhor que Redshift , BigQuery e Azure
- MinIO (Storage)

## Namespace

Organizacao Logica, nao utilizar default

## ArtifactHub

Helm utiliza os charts do artifact.


## MinIO

- Object Storage Compatible
- Gateway: AWS S#, GCS, Azure
- Notification Event

185 Gb/s (2x mais rapido S3)

##

Pinot - Clickhouse - Druid