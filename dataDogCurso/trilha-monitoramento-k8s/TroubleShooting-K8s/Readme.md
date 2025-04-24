# Estratégia de Troubleshooting

Problemas em aplicações voltadas para o usuário podem ter origens em diversos pontos — desde DNS, passando pelo plano de controle do cluster, até o código da aplicação. As ferramentas do **Datadog** ajudam você a identificar a **causa raiz** e resolvê-la rapidamente, especialmente quando você segue uma abordagem de troubleshooting bem estruturada.

---

## Estratégia Geral

A estratégia que você usará para solucionar problemas neste curso é:

### 1. Reproduzir o Problema
Você precisa **reproduzir o problema** para entender sua origem e verificar se a solução proposta realmente resolve a questão.

---

### 2. Investigar de Cima para Baixo
Comece pela **camada mais abstrata** e vá descendo até o nível da aplicação.

No curso, a sequência será:

- **Kubernetes Overview**
- **Kubernetes Explorer**
- Dashboards do Kubernetes
- Nível de serviço (pods, containers, etc.)

---

### 3. Identificar a Causa Raiz
Use os detalhes dos pods, dos serviços, **logs** e **APM** para encontrar a **causa raiz** do problema.

> 🔁 Às vezes, as pistas encontradas nesse nível farão você voltar uma etapa para investigar por outro caminho.

---

### 4. Resolver o Problema
Resolva o problema ou encaminhe para o time responsável, junto com os resultados da sua investigação.

> 🧩 Links para visões no **Log Management** e no **APM** ajudam a fornecer o contexto necessário.

---

### 5. Confirmar a Correção
Observe se os **sintomas desapareceram** após a correção. Verifique se os **sinais no Datadog** voltaram ao normal.

---

### 6. Criar Monitores
Crie **monitores** para alertá-lo caso o problema volte a ocorrer futuramente.

---

## Dica Final

Cada cenário de troubleshooting é **único** e pode te levar por caminhos inesperados. Essa estratégia pode não servir para todos os casos — ou mesmo para a maioria deles.

> 🧠 O mais importante é ser **consistente** na abordagem e entender como as ferramentas do **Datadog** podem te ajudar em cada etapa.
