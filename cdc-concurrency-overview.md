# CDC e Concurrency Control: Integrando Estratégias Arquiteturais

Este documento complementa a discussão sobre controle de concorrência (otimista vs pessimista) com insights técnicos sobre Change Data Capture (CDC), incluindo exemplos práticos.

---

## 📌 Change Data Capture (CDC)

**CDC** é um padrão para detectar e propagar alterações (inserções, atualizações, deleções) em dados fonte para sistemas consumidores de forma incremental.

### Principais métodos

1. **Polling por timestamp/version**  
   - Usa colunas como `last_updated` ou `version_number` para detectar mudanças.  
   - *Trade-offs*: simples, mas não captura deleções, tem latência e pode sobrecarregar o BD.

2. **Triggers**  
   - Utiliza triggers que gravam alterações em tabelas auxiliares.  
   - *Trade-offs*: latência reduzida, porém aumenta carga de escrita e complexidade.

3. **Log-based (WAL/binlog mining)**  
   - Lê o log de transações do BD (WAL em Postgres, binlog em MySQL).  
   - *Trade-offs*: mínimo overhead no BD, baixa latência, porém requer parsing de logs e componentes adicionais.

### Outras técnicas

- **Status column**: flag de alteração; úil como filtro adicional.  
- **Combinação poderosa**: timestamp + version + status.

---

## 🔄 Relação com Concurrency Control

### Otimista 📈  
- Similar ao CDC: ambos assumem que conflitos são raros.  
- Na concorrência: valida leitura antes do commit; no CDC: captura incremental sem bloqueio.

### Pessimista 📉  
- Usa locks *on-the-fly*, diferente do CDC que foca em detecção pós-transação.  
- Em sistemas com alta contenção, CDC log-based evita travamento, mas não resolve conflitos lógicos.

---

## ⚖️ Trade-offs do CDC

| Método         | Overhead no BD | Latência      | Captura de deletes | Complexidade |
|----------------|----------------|---------------|---------------------|--------------|
| Polling        | Médio–alto     | Alta (batch)  | ❌ Só soft delete   | Baixa        |
| Triggers       | Alto           | Baixa         | ✅ Total            | Média–alta   |
| Log-based      | Baixo          | Muito baixa   | ✅ Total            | Alta         |

---

## 🪩 Exemplos de Integração

### Exemplo 1: Estoque com Lock Otimista
- Leitura do estoque com versão (`version`).
- `UPDATE produtos SET quantidade = ?, version = version+1 WHERE id = ? AND version = ?`.
- CDC log-based publica eventos de alteração para sistemas de notificação e BI.

### Exemplo 2: Sistema financeiro com lock pessimista
- `SELECT saldo FROM contas WHERE id = ? FOR UPDATE`
- Garante consistência sob concorrência forte.
- CDC registra movimentações para auditores e replicadores downstream.

### Exemplo 3: Integração legado com polling
- Sistema legado atualiza tabela `clientes` com `last_updated`.
- Job batch executa `SELECT * FROM clientes WHERE last_updated > ?`
- Simples e eficaz em ambientes com baixa concorrência.

---

## 🪩 Integração Arquitetural

- Combine CDC log-based com **event-driven architecture** para propagar eventos (ex: via Kafka), integrando com **otimistic concurrency control** nos consumidores.  
- Use CDC em esquemas **CQRS/Event Sourcing** para manter repositórios de consulta ou replicação.  
- Em sistemas com alta contenção de escrita, use **CDC + locking seletivo** (pessimista) para evitar race conditions críticas.

---

## ✅ Recomendações

- Prefira **CDC log-based** quando precisar de replicação em tempo real com mínimo impacto operacional.  
- Em áreas de sistema com pouca contenção, mescle otimistic lock e CDC para balancear performance e consistência.  
- Em operações críticas com concorrência elevada (ex: finanças), mantenha controle pessimista + backups via CDC.  
- Garanta **observabilidade no pipeline CDC**, incluindo métricas de latência, falhas e contagem de eventos.

---

## 🌟 Quando adotar cada tática

- **CDC log-based + Kafka + consumidores com optimistic lock**: alta escalabilidade + consistência eventual.
- **Triggers + pessimista**: quando é necessária consistência imediata em escrita, mas o custo de locks é aceitável.
- **Polling**: aceitável apenas em cenários de baixa criticidade e tolerância à latência.

---

## 📚 Referências

- Wikipedia – Change Data Capture  
- Confluent Blog – CDC para event streams  
- Striim – Impacto no DB e log mining

---
