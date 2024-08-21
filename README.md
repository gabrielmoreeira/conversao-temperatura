# Projeto conversão de temperatura

### Sobre o projeto
O projeto conversão de temperatura é um projeto desenvolvido em NodeJS. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando NodeJS.

### Observações do projeto
A aplicação é exposta usando a porta 8080


### Kubernets
kubectl apply -f k8s/deployment.yaml && watch 'kubectl get pod'  
kubectl rollout history deployment conversao-temperatura
kubectl rollout undo deployment conversao-temperatura && watch 'kubectl get pod'

> Deploy - Do menor para o maior
1 Pod - Menor objeto do kubernets
2 Replicaset - Garante a quantidade de replicas, que irá estar em execução
3 Deployment - gerencia o replicaSet, responsável pela atualização do replicaSet
4 Service
  4.1 - ClusterIP - Utilizado internamente do cluster Kubernetes, ou seja, somente é acessivel de dentro do cluster Kubernetes
  4.2 - NodePort - Tornar acessivel externamente - Mais usados em ambientes onPremises
  4.3 - LoadBalancer - Criar um IP de acesso externo(Publico) Obs.: Mais usados em Clouds Providers


### K3D
k3d cluster list
k3d cluster delete "nome cluster"
k3d cluster create meucluster --servers 3 --agents 3 -p 30000:30000@loadbalancer
k3d cluster create meucluster --servers 1 --agents 1 -p 30000:30000@loadbalancer

### Docker
docker build -t gabrielmoreeira/conversao-temperatura:v2 --push .