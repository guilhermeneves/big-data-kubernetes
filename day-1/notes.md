# Intro

Empresas que fizeram transicao onprem para nuvem na maioria aumentaram o valor.

Virtualizacao de maquinas virtuais.

Repo do treinamento: https://github.com/luanmorenomaciel/big-data-on-k8s

Monolitico vs Microservicos -

Microservicos separaram as databases facilitou o trabalho do dev para quebrar em pequenos servicos porem distribui os dados da empresa, por isso, a parte de dados e essencial para trazer esses dados de uma forma org.

## Service Mesh

Como aplicacoes dentro de containers se comunicam. Abstrai a complexidade da configuracao. (orquestra micro servicos)
O ISTIO e a ferramenta mais famosa para service mesh.

## Data Mesh

Coracao do Mesh no data mesh e o Kafka.


## Maquinas Virtuais e Containers

Na maquina virtual temos o hypervisor (por volta 2007) entre as VMs e sua Maquina. (Pacotes e versoes compartilhados)
Containers por outro lado separamos o sistema operacional. (Docker roda sobre o sistema operacional)


Docker: Conteinazacao ja existia a muito tempo no linux, porem o Docker conseguiu distribuir e empacotar isso.

Docker Desktop (Camada de virtualizacao de container)
Docker Hub (Repositorio de Imagem)
Docker-Compose: Compor varios containers, atomiza o processo como unidade.
Docker-Swarm: Orquestrator de containers, ele vai balancear os containers.
Docker-Volume: COmpartilhar informacao entre container , pois container eh efemero.


## Stateless & Stateful

Stateless nao salva dados, Stateful salva dados.

COntainers podemos ter volumes efemeros e nao efemeros.

Um volume criado no Docker nao stateful, pois quando reinicia perde os dados.

Estado 'e armazenar estado persistentemente em disco.

## Orchestration Enginer

Google desenvolveu o Kubernetes.

- Docker Swarn
- Openshift ('e Kubernetes encapsulated pela RedHat ** Muito caro)
- Kubernetes

## Kubernetes Conceito

Cloud Native: COntainer, DevOPs e Criacao da cloud

Kubernetes Definicao

Self Healing InfraStructure Backbone System

- Load Balancer interno
- Self healing
- Vault
- etc...

### Cluster Architecture - Control Plane and Nodes

Kubernetes arquitetura distribuida, master slave.
Control Plane- master
Worker Nodes - Slave

COntrol PLane
- API Server - recebe calls get, post...
- Etcl - Key/value DB like Redis
- Scheduler - Faz o check de tempos em tempos nao definido na literatura, sobre as necessidades dos nodes e cluster como helath check
- Kube-controller: Controla o cluster kubernetes e modos de deploy
- Cloud-Controller: Usa recursos da nuvem especifica fora do K8s

WorkerNode (Run Pods)
- Kubelet
- KubeProxy
- Container Runtime: Docker, RKT, CRI-O - Docker foi marcado como Deprecated, sera substituido por CRI
- kubectl - CLI to interact with K8s objects

Pods

Small Execution Unit in Kubernetes **Not Container and Applications) hard limit 1000 pod por worker node.
O pod tem um manifesto podemos comparar com o docker-compose

Nao fazemos geralmente deployment com tipo pod, mas com workload, pois no pod nao tem como garantir o gerenciamento do POD por work node.

5 estados que ele pode estar = 

- pending: aceito pelo cluster mas esperando
- running: vinculado por um no (scheduler nunca vai mexer em um pod que esta running)


Workloads (Kind)

- DaemonSet: Um grupo de pods replicados, vai criar um pod em cada worker node automatimcanente sem precisar especificar. FLuentDB e um exemplo. geralmente usado para monitraomento. Cuidado com a escala, pois o daemonset e recomendado apenas para poucos casos de monitoramento, para aplicacoes nao seria possivel escalar os pods./
- Deployment & ReplicaSet: Nesse modo podemos especificar a quantidade de replicas ou seja diferente do Daemonset ao inves de 1 posso adicionar 3 ou 4. porem 1 replica no ReplicaSet significa apenas 1 pod e nao 1 pod por WorkerNode.
- StatefulSet: Pods with Sticky Identity and Persistent Storage. QUando quero guardar persistencia de dados mesmo apos restart. Esse workload trabalha exatamente da forma ReplicaSet, porem com stateful.
- Job: Vai rodar x vezes assim que executado
- CronJob: 'e possivel agendar o job usando cron, ele roda o pod e depois mata.

Servicos

'e um tipo

ClusterIP > Trafego intra cluster, comunicacao entre os pods
NodePOrt -> Acesso externo nao muito utilizado
LoadBalancer -> Muito utilizado, usa o LB da nuvem (vc paga pelo loadbalancer dependendo do que vc entrega para fora mais interesante ingress)

Ingress

Gerencia acesso externo ao cluster > (NGNIX, COnsul, Trafik sao Ingress)
Cria uma tabela e manda para o servico correto conforme acesso externo ()

nao sao todas as aplicacoes que funcionam muito bem com ingress./

Volumes & Types

Um pod pode ter um emptyDir um diretorio que os containers compartilham e que e efemero. (quando movimentar os dados ele e apagado)

Temos tipo de volume no Kubernetes e podemos usar EBS, Container Storage Interface, Single Persistent Disk, Azure Disk.
CSI (container storage interface) foi criado pela CNCF e 

ConfigMap e Secrets

salva env vars e secrets no kubernetes

## Kubeclt

command line interface para gerenciar o cluster

## Self Hosted Kubernetes

Voce precisa de muitos itens, backup, gerenciamento, sso, maquinas virtuais.
1 milhao de dolares em salario engenharia (fonte twitter) nao fa;a isso.

## Cloud Kubernetes

Verifique se [e certified Kubernetes] entao pode ser qualquer provedor./

Azure AKS (unico que nao cobra control plane), Google GKE, AWS EKS

## IaC for DataEngineers

Terraform 'e agnostico a nuvem/.

Terraform Registry -> providers trazem exemplos de uso para aplicacao
Terraform Init - traz os dados do provedor
terraform plan - plano de execucao o que vai fazer
terraform apply

## BigData on Kubernetes

2009 - onprem hadoop com forneecdores especificos (cloudera,etc..)
2014 - nuvem paas e saas
2018 - K8s for apps & data

https://dokcommunity.slack.com/

## StorageClass

Storage Class, Persistent Volume, Persistence Volume Claim

SC = tipo de storage e ele e atrelado a um cluster

um nivel acima do SC 'e o PD (persisten volume) 

SC -> PV (abstrai o layer storage) -> PVC (faz o pedido do espaco)

No CSI 'e mais facil expandir os discos.

## Development Environment

- MiniKube ( ou microK8s, Kind, K3D)
- DigitalOcean ou Linode

## Package Manager

Helm

Ao inves de gerenciar varios yamls utilizar helm

Kustomize

Package manager nativo, pode customizar sequencia de scripts mais custom que helm 
(Artifacthub.io)


