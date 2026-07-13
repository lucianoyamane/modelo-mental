# Máquinas de Estado: Boas Práticas de Modelagem

## 📘 Visão Geral

Uma **máquina de estado** (FSM – Finite State Machine) é uma estrutura formal usada para modelar o comportamento de sistemas com base em:

- Um **conjunto finito de estados** possíveis
- Um **estado inicial**
- Um **conjunto de eventos** que causam transições
- Uma **lógica de transição**
- Ações associadas às transições (opcional)

---

## ✅ Boas Práticas de Estruturação

### 1. Modelagem explícita de estados e eventos

- **Estados** e **eventos** devem ser representados como **tipos explícitos** (ex: classes ou enums bem nomeados).
- Evite usar strings soltas ou enums com significados mistos.

### 2. Separar transição da lógica de efeito colateral

- A FSM deve apenas determinar o próximo estado.
- Efeitos colaterais (notificações, comandos, eventos externos) devem ser tratados separadamente.

### 3. Transições como estrutura de dados

- Tabelas de transição ou pattern matching devem ser usados para tornar as transições declarativas.

### 4. Orientação a comportamento

- O comportamento deve depender do **estado atual**.
- Modelagem baseada em **validação de ações possíveis por estado**.

### 5. Imutabilidade

- FSMs devem ser **puras**: dado um estado e um evento, sempre produzir o mesmo próximo estado.

### 6. FSM vs Workflow

- FSM: transições simples e focadas em estado.
- Workflow engine: fluxos longos, com múltiplas etapas, atores ou persistência de passo a passo.

---

## 🔍 Diferença entre Estado e Evento

| Conceito  | Estado 🟦                              | Evento 🟧                             |
|-----------|----------------------------------------|--------------------------------------|
| O que é   | Condição persistente                  | Ocorrência pontual                   |
| Tempo     | Duradouro                             | Efêmero                              |
| Exemplo   | Pedido em `CONFIRMADO`                | `PagamentoConfirmado`                |
| Modelagem | Atributo de uma entidade               | Entrada externa ou fato de sistema   |
| Validade  | Um único estado por vez                | Múltiplos eventos possíveis          |

---

## 🎯 Critérios para definição

### Para Estados

- **Irreversíveis** (se final)
- **Semântica clara** e **ação esperada**
- Não redundantes
- Exemplo de estado final: `EXPIRADO`, `CANCELADO`, `PAGO`

### Para Eventos

- Verbos no passado (ex: `PagamentoRecebido`)
- Devem representar **fatos concretos**
- Não confundir com mudanças de status

---

## 🚫 Más práticas comuns

```java
enum Status {
  PAGAMENTO_RECEBIDO, /* evento disfarçado */
  CANCELAMENTO_SOLICITADO /* evento disfarçado */
}
```

---

## 🧩 Encerramento explícito de fluxo

### Problema comum

- Entidades que nunca chegam a um **status final**
- Ex: boletos `EMITIDOS` que nunca são pagos nem marcados como vencidos

### Estratégias para mitigar

- Modelar estados finais claros (`EXPIRADO`, `CANCELADO`)
- Implementar eventos baseados em tempo (ex: `BoletoExpirado`)
- Ter ownership claro do encerramento
- Monitorar entidades em aberto por muito tempo

---

## 💡 Padrões do repositório modelo-mental

- **“Parse, don’t validate”**: transforme eventos externos em modelos internos válidos.
- **“Consumidor adapta, não fonte”**: o estado do domínio deve ser derivado dos eventos, não o contrário.
- **Comportamento como contrato**: definir explicitamente como e quando o fluxo se encerra.

---

## 📄 Exemplo de FSM para pedido

```java
enum PedidoStatus {
  CRIADO, CONFIRMADO, CANCELADO
}

sealed interface PedidoEvento {}

record PagamentoConfirmado(String pedidoId) implements PedidoEvento {}
record CancelamentoSolicitado(String pedidoId, String motivo) implements PedidoEvento {}

PedidoStatus proximoEstado(PedidoStatus atual, PedidoEvento evento) {
  return switch (atual) {
    case CRIADO -> switch (evento) {
      case PagamentoConfirmado _ -> CONFIRMADO;
      case CancelamentoSolicitado _ -> CANCELADO;
      default -> throw new IllegalStateException();
    };
    case CONFIRMADO, CANCELADO -> throw new IllegalStateException("Estado final");
  };
}
```

---

## 📌 Template para documentação de encerramento de fluxo

```markdown
### Comportamento esperado para boletos

- Após emissão, o boleto deve terminar em um dos seguintes estados:
  - `PAGO`: evento `PagamentoRecebido`
  - `EXPIRADO`: vencimento ultrapassado sem evento de pagamento
  - `CANCELADO`: evento explícito de cancelamento

- Regra de vencimento:
  - A cada 24h, executar job de verificação de vencimento
  - Se `hoje > dataVencimento` e status == EMITIDO → gerar evento `BoletoExpirado`
```
