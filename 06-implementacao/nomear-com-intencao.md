# Nomear com Intenção

## Contexto

Nomes são parte do design. Eles moldam a teoria que o leitor constrói sobre o sistema e reduzem ou aumentam a carga cognitiva necessária para modificar o código.

Um nome ruim obriga o leitor a inspecionar implementação. Um nome bom comunica papel, comportamento e limite.

## Princípio

Nomeie conceitos pelo significado que possuem no domínio, não pelo detalhe técnico usado para implementá-los.

## Critérios

* O nome explica intenção antes de explicar mecanismo.
* O nome pertence à linguagem do domínio quando representa regra de negócio.
* O nome revela comportamento observável.
* O nome evita termos genéricos como `process`, `handle`, `manager` e `helper` quando eles escondem responsabilidades distintas.
* O nome não promete mais estabilidade ou generalidade do que o conceito realmente possui.

## Exemplos

```java
// Fraco
doWork();

// Melhor
grantAccess(user);
```

```java
// Fraco
boolean valid;

// Melhor
boolean customerCanReceiveCredit;
```

## Relações

* [Código como Design](../01-fundamentos/codigo-como-design.md)
* [Refactoring](./refactoring.md)
* [Comportamento Antes da Estrutura](../03-modelagem/comportamento-antes-da-estrutura.md)
