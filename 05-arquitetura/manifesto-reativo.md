# Manifesto Reativo: Princípios e Trade-offs Arquiteturais

O [Manifesto Reativo](https://www.reactivemanifesto.org/pt-BR) propõe uma abordagem para o design de sistemas distribuídos modernos, baseada em quatro princípios:

1. **Responsivo**
2. **Resiliente**
3. **Elástico**
4. **Orientado a mensagens**

Este documento detalha esses princípios e discute os principais trade-offs envolvidos na adoção de uma arquitetura reativa.

---

## 1. Responsivo

### Objetivo
Garantir que o sistema responda em tempo hábil, fornecendo feedback consistente aos usuários e sistemas integrados.

### Trade-offs
- **➗ Custo em observabilidade:** exige boas ferramentas de tracing e monitoramento (ex: OpenTelemetry, Jaeger).
- **➗ Sobrecarga com timeouts, retries e circuit breakers:** manter responsividade sob falha requer complexidade operacional.

---

## 2. Resiliente

### Objetivo
Manter o sistema responsivo mesmo diante de falhas parciais.

### Práticas comuns
- Isolamento de componentes (bulkheads)
- Tolerância a falhas com fallback e retries
- Replicação de dados, supervisionamento (ex: supervision tree no Akka)

### Trade-offs
- **➗ Complexidade no teste de falhas:** simular e validar comportamento resiliente pode ser custoso.
- **➗ Latência de recuperação:** fallback pode oferecer dados degradados ou desatualizados.

---

## 3. Elástico

### Objetivo
Ajustar recursos dinamicamente conforme a demanda.

### Práticas comuns
- Horizontal scaling
- Auto-scaling com base em métricas (ex: Prometheus + KEDA)
- Arquitetura stateless

### Trade-offs
- **➗ Custo de infraestrutura dinâmica:** consumo de recursos pode oscilar e afetar custos na nuvem.
- **➗ Dificuldade em manter estado consistente:** distribuição de carga exige reengenharia de sessão e dados compartilhados.

---

## 4. Orientado a mensagens

### Objetivo
Promover o desacoplamento através de comunicação assíncrona entre componentes.

### Práticas comuns
- Kafka, RabbitMQ, NATS
- Event sourcing e CQRS
- Estratégias de coreografia e orquestração

### Trade-offs
- **➗ Debug e rastreamento mais difícil:** sequenciar eventos distribuídos é desafiador.
- **➗ Consistência eventual:** muitas vezes é necessário abrir mão de consistência forte.
- **➗ Entrega duplicada ou fora de ordem:** exige idempotência e reprocessamento seguro.

---

## Quando adotar?

| Cenário | Reativo é recomendado? |
|--------|-----------------------|
| Alta concorrência e disponibilidade | ✅ Sim |
| Domínio com eventos naturais (ex: financeiro, logística) | ✅ Sim |
| Sistemas internos com baixa carga | ❌ Adotar parcialmente |
| Sistemas monolíticos legados | ⚠ Adoção incremental |

---

## Recomendação arquitetural

- Utilize os princípios reativos como **direção**, não como fim.
- Evite migrar para mensageria ou event-driven apenas por tendência.
- Avalie o impacto nos **tempos de resposta, capacidade de operação, e manutenção**.
- Adote **observabilidade desde o início** — não é opcional em sistemas reativos.

---

## Referências
- https://www.reactivemanifesto.org/pt-BR
- https://martinfowler.com/articles/reactive.html

