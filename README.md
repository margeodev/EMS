# Especialista Micro Serviços

## Aula 7.9

# Microserviços Orientados a Business Capabilities

Principais características de uma arquitetura de microserviços alinhada a capacidades de negócio (*Business Capabilities*), seguindo Domain-Driven Design (DDD) e boas práticas de autonomia.

---

## 🎯 **Características Principais**

### 1. **Alinhamento com o Domínio de Negócio**
- Cada microserviço representa uma **capacidade de negócio específica** (ex.: pedidos, clientes, pagamentos).
- Utiliza **Bounded Contexts (DDD)** para delimitar responsabilidades.
- Exemplo: 
  - `servico-pagamentos`: gerencia apenas transações financeiras.

### 2. **Autonomia (Independência)**
- Dono do próprio banco de dados e código.
- Implantação e escalabilidade independentes.
- Comunicação via APIs (REST/gRPC) ou mensageria (Kafka/RabbitMQ).

### 3. **Baixo Acoplamento**
- Sem compartilhamento direto de banco de dados ou bibliotecas.
- Interfaces estáveis (APIs) garantem isolamento.

### 4. **Escalabilidade Seletiva**
- Serviços críticos podem ser escalados sob demanda.
- Exemplo: `servico-estoque` pode ser replicado em promoções.

### 5. **Tecnologia Adequada ao Problema**
- Linguagens e bancos de dados heterogêneos.
- Exemplo:
  - `servico-analise-dados`: Python + MongoDB.
  - `servico-transacoes`: Java + PostgreSQL.

### 6. **Propriedade pela Equipe (Team Ownership)**
- Equipes multidisciplinares ("You build it, you run it").
- Cultura DevOps e entrega contínua.

### 7. **Resiliência a Falhas**
- Circuit Breaker, retry policies e fallbacks.
- Falhas não propagam (ex.: `servico-recomendacoes` falha, mas `servico-catalogo` continua).

### 8. **Monitoramento e Rastreabilidade**
- Logs centralizados (ELK), métricas (Prometheus) e traces (Jaeger).

---

## 📊 **Exemplo Prático: E-commerce**

| **Business Capability**       | **Microserviço**           | **Tecnologia**        |
|-------------------------------|----------------------------|-----------------------|
| Gerenciamento de Usuários     | `servico-usuarios`         | REST API (Node.js)   |
| Processamento de Pedidos      | `servico-pedidos`          | Kafka Events (Java)  |
| Pagamentos                   | `servico-pagamentos`       | gRPC (Go)            |
| Recomendações                 | `servico-recomendacoes`    | Python (ML)          |

---

## 🔑 **Boas Práticas**
- Evite **nanosserviços** (granularidade excessiva).
- Documente contratos de API (OpenAPI/Swagger).
- Use **service mesh** (Istio, Linkerd) para gerência de tráfego.

---

## 📚 **Referências**
- Livro: *Building Microservices* (Sam Newman).
- Padrão: *Domain-Driven Design* (Eric Evans).

---
