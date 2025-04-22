# Componentes do Plano de Controle do Kubernetes

O plano de controle gerencia os nós e pods em um cluster. Ele é composto pelos seguintes componentes:

- **API Server**
- **Controller Manager**
- **Scheduler**
- **etcd**

Em ambientes em nuvem, um **Cloud Controller Manager** também pode fazer parte do plano de controle.

---

## API Server

O **API Server** é a entidade central de gerenciamento do cluster. Ele atua como a interface principal do plano de controle do Kubernetes e como ponto de entrada para o gerenciamento do cluster. 

Ele valida e configura os dados dos objetos da API, como:

- Pods  
- Serviços  
- Controladores de replicação  
- Entre outros

**Problemas comuns:**

- Altas taxas de requisição
- Altas taxas de erro
- Alta latência

Esses sintomas podem indicar sobrecarga ou má configuração do API Server.

---

## Controller Manager

O **Controller Manager** monitora continuamente o estado do cluster por meio do API Server e tenta corrigir quaisquer desvios. Esse processo é conhecido como *reconciliation loop* (laço de reconciliação).

Ele executa uma coleção de controladores, como:

- **Node Controller**
- **Replication Controller**
- **Endpoints Controller**

Cada um é responsável por aspectos específicos do gerenciamento do cluster.

**Problemas comuns:**

- Discrepâncias no estado do cluster
- Status dos nós instáveis
- Pods que não iniciam
- Pods que não estão sendo replicados corretamente

---

## Scheduler

O **Scheduler** é responsável por alocar pods nos nós do cluster. Ele considera diversos fatores ao tomar decisões de alocação, como:

- Requisitos de recursos
- Restrições de hardware
- Regras de afinidade e anti-afinidade

**Problemas comuns:**

- Pods presos no estado `Pending`
- Pods que não estão sendo alocados
- Pods alocados em nós com recursos insuficientes

---

## etcd

O **etcd** é um armazenamento distribuído de chave-valor que guarda:

- Dados de configuração
- Estado do cluster
- Metadados

Ele é a **fonte de verdade** do cluster, utilizado pelos componentes do plano de controle para armazenar e recuperar dados.

**Problemas comuns:**

- Alto uso de disco
- Alta latência
- Altas taxas de erro

Esses problemas podem causar falhas em agendamentos e atualizações.

---

# Configurações do Plano de Controle

O plano de controle pode operar em diferentes arquiteturas, dependendo do ambiente:

## Kubernetes Gerenciado

Em serviços gerenciados como:

- Amazon EKS
- Google GKE
- Azure AKS

O plano de controle é gerenciado pelo provedor de nuvem. A interação acontece via API ou CLI da nuvem. Esses componentes também emitem dados de telemetria que podem ser monitorados.

## Fora do Cluster

Em ambientes on-premises ou autogerenciados, os componentes do plano de controle podem rodar **fora** do cluster, comunicando-se com os nós pela rede.

## Dentro do Cluster

Em clusters pequenos ou de nó único, os componentes do plano de controle podem rodar **como containers dentro do próprio cluster**.

# Coleta de Telemetria dos Componentes do Plano de Controle

Coletar dados de telemetria dos componentes do plano de controle é essencial para monitorar a **saúde** e o **desempenho** do seu cluster Kubernetes.

---

## kube-state-metrics

O **kube-state-metrics** é um projeto open source que escuta o **API Server** do Kubernetes e gera métricas sobre o estado dos objetos no cluster.

Ele fornece informações como:

- Quantidade de pods
- Deployments
- Outros recursos do cluster

> ✅ O Agente do Datadog já possui uma verificação integrada para o kube-state-metrics, então **não é necessário instalá-lo separadamente**.

---

## kubelet e CRI

O Agente também possui verificações integradas para o **kubelet** e para a **Container Runtime Interface (CRI)**.

Essas verificações coletam métricas sobre:

- Nós (nodes)
- Pods
- Containers

---

## Integrações com o Datadog

O **Datadog** se integra com os componentes do plano de controle do Kubernetes para coletar **métricas** e **logs**. É possível monitorar a saúde e o desempenho dos seguintes componentes:

- API Server
- Controller Manager
- Scheduler
- etcd

Além disso, o Datadog detecta automaticamente serviços comuns e instala suas integrações para habilitar:

- Coleta de métricas
- Coleta de logs
- Dashboards prontos para uso

**Exemplos de serviços integrados automaticamente:**

- PostgreSQL
- Redis
- Nginx
- Centenas de outros

---

## Logs

Você pode visualizar os **logs** dos componentes do plano de controle e dos workloads no Datadog.

Os logs ajudam a:

- Identificar e resolver problemas
- Entender o comportamento dos componentes

---

## Métricas de Aplicações

Além dos componentes do plano de controle, também é possível coletar métricas dos **workloads** executando no cluster.

Você pode **instrumentar suas aplicações** com as bibliotecas de tracing do Datadog para:

- Coletar **traces distribuídos**
- Correlacionar com **métricas** e **logs**
