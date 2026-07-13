
# Lei de Demeter (Princípio do Mínimo Conhecimento)

> "Fale apenas com seus amigos diretos."

## 🎯 Propósito

Registrar a importância e aplicação da **Lei de Demeter** como um princípio de desenvolvimento que prioriza baixo acoplamento, encapsulamento e facilidade de manutenção.

Baseado no artigo:  
👉 [Lei de Demeter – dev.to/ino_gu](https://dev.to/ino_gu/lei-de-demeter-4ldf)

---

## 🔍 O que é a Lei de Demeter?

A Lei de Demeter estabelece que um objeto deve interagir **somente com seus colaboradores diretos** e não com os colaboradores dos seus colaboradores.

### ✅ Um método deve se comunicar com:
- Ele mesmo;
- Seus parâmetros;
- Seus atributos (componentes diretos);
- Objetos que ele cria internamente;
- Variáveis locais.

---

## 🚩 Como violamos a Lei?

### 🔥 Violação comum:
```js
const data = cliente.ultimoPedido.dadosPedido.dataEmissao;
```

### ✅ Correto segundo LoD:
```js
const data = cliente.getDataEmissao();
```

---

## 🎯 Benefícios
- Reduz acoplamento.
- Aumenta o encapsulamento.
- Facilita a manutenção.
- Melhora a testabilidade.
- Reduz carga cognitiva.

## ⚠️ Desvantagens/Trade-offs
- Criação de muitos métodos "delegadores".
- Interfaces das classes podem crescer.
- Risco de burocratizar código simples.

---

## 💡 Boas práticas associadas

- 🗣️ **Tell, Don’t Ask:** Faça o objeto agir, não pergunte seu estado.
- 🔐 **Encapsulamento forte:** Proteja dados e comportamentos.
- ⚖️ **CQS (Command Query Separation):** Separe comandos e consultas.
- 🚫 **Evite Primitive Obsession:** Prefira objetos ricos a dados soltos.
- 🧠 **Reduza carga cognitiva:** Código mais linear, sem navegações profundas.

---

## 🔥 Exemplos Práticos

### ❌ Errado:
```java
if (pedido.getStatus().equals("APROVADO")) {
    pedido.getCliente().getEndereco().getRua();
}
```

### ✅ Correto:
```java
if (pedido.estaAprovado()) {
    pedido.getEnderecoDeEntrega();
}
```

---

## 🧠 Tópicos Relacionados

- YAGNI (You Ain’t Gonna Need It)
- Tell, Don’t Ask
- Primitive Obsession
- Encapsulamento forte
- Design orientado a comportamento
- CQS (Command Query Separation)
- DRY, mas com responsabilidade

---

## 📜 Referência

- [Lei de Demeter – dev.to/ino_gu](https://dev.to/ino_gu/lei-de-demeter-4ldf)

---

## 🚀 Conclusão

A Lei de Demeter não é uma regra rígida, mas uma diretriz poderosa para manter sistemas evolutivos, com baixo acoplamento, alta coesão e fácil manutenção.

> 🧠 **"Fale com seus amigos, não com estranhos."**
