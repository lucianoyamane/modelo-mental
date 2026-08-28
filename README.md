# Modelo Mental

Este repositório reúne modelos mentais para tomada de decisões arquiteturais.

O objetivo não é manter uma coleção de boas práticas isoladas. A proposta é organizar um modo de raciocinar sobre software: entender o problema, explicitar trade-offs, modelar comportamento, proteger fronteiras, reduzir acoplamento e documentar decisões que permitam evolução contínua.

## Filosofia

Arquitetura não é a arte de desenhar sistemas. É a disciplina de melhorar a qualidade das decisões que constroem e evoluem esses sistemas.

Os documentos partem de algumas premissas:

* Arquitetura melhora decisões.
* Boa arquitetura reduz o custo de revisar decisões.
* Toda decisão possui trade-offs.
* Complexidade não desaparece; ela muda de lugar.
* Quando não podemos prever com segurança, devemos projetar para aprender.
* O consumidor adapta; a fonte permanece estável.
* Comportamento revela conhecimento.
* Eventos representam fatos, não comandos.
* Contratos explícitos envelhecem melhor que dependências implícitas.
* Simplicidade reduz carga cognitiva.
* Código é design executável.
* Documentação deve apoiar decisões, não apenas registrar estruturas.

## Fluxo de Leitura

```text
Fundamentos
    ↓
Heurísticas
    ↓
Modelagem
    ↓
Integração
    ↓
Arquitetura
    ↓
Implementação
    ↓
Comunicação e Times
    ↓
Estudos de Caso
```

## Estrutura

```text
01-fundamentos/
02-heuristicas/
03-modelagem/
04-integracao/
05-arquitetura/
06-implementacao/
07-comunicacao-e-times/
08-estudos-de-caso/
```

## 01. Fundamentos

Base conceitual do repositório.

* [Arquitetura como Decisão](./01-fundamentos/arquitetura-como-decisao.md)
* [Decisão sob Incerteza](./01-fundamentos/decisao-sob-incerteza.md)
* [Complexidade e Trade-offs](./01-fundamentos/complexidade-e-trade-offs.md)
* [Simplicidade como Sofisticação](./01-fundamentos/simplicidade-como-sofisticacao.md)
* [Código como Design](./01-fundamentos/codigo-como-design.md)
* [Abstração Prematura](./01-fundamentos/abstracao-prematura.md)

## 02. Heurísticas

Atalhos mentais para decisões em contexto de incerteza.

* [Heurísticas Arquiteturais](./02-heuristicas/heuristicas-arquiteturais.md)
* [Maus Hábitos Técnicos](./02-heuristicas/maus-habitos-tecnicos.md)

## 03. Modelagem

Documentos sobre comportamento, domínio, estados, eventos e tradução de dados externos para modelos internos válidos.

* [Comportamento Antes da Estrutura](./03-modelagem/comportamento-antes-da-estrutura.md)
* [BDD](./03-modelagem/bdd.md)
* [Máquinas de Estado](./03-modelagem/finite-state-machine.md)
* [Parse, Don't Validate](./03-modelagem/parse-dont-validate.md)
* [Entidades Técnicas vs Entidades de Negócio](./03-modelagem/entidades-tecnicas-vs-entidades-de-negocio.md)

## 04. Integração

Como contextos se relacionam sem perder autonomia.

* [Acoplamento](./04-integracao/acoplamento.md)
* [Source e Translation](./04-integracao/source-e-translation.md)
* [Arquitetura Fonte da Verdade](./04-integracao/arquitetura-fonte-da-verdade.md)
* [Eventos Representam Fatos](./04-integracao/eventos-representam-fatos.md)
* [Contratos e Versionamento](./04-integracao/contratos-e-versionamento.md)
* [CDC e Concorrência](./04-integracao/cdc-e-concorrencia.md)

## 05. Arquitetura

Decisões sistêmicas, fronteiras, documentação arquitetural e operação.

* [Ortogonalidade](./05-arquitetura/ortogonalidade.md)
* [Lei de Conway e Fronteiras](./05-arquitetura/lei-de-conway-e-fronteiras.md)
* [Manifesto Reativo](./05-arquitetura/manifesto-reativo.md)
* [Observabilidade](./05-arquitetura/observabilidade.md)
* [ADR](./05-arquitetura/adr.md)
* [C4 Model](./05-arquitetura/c4-model.md)

## 06. Implementação

Como os princípios aparecem no código.

* [Refactoring](./06-implementacao/refactoring.md)
* [Lei de Demeter](./06-implementacao/lei-de-demeter.md)
* [Nomear com Intenção](./06-implementacao/nomear-com-intencao.md)
* [Imperativo vs Declarativo](./06-implementacao/imperativo-vs-declarativo.md)

## 07. Comunicação e Times

Práticas que sustentam decisões coletivas, senioridade técnica e colaboração.

* [Maturidade Técnica e Carreira](./07-comunicacao-e-times/maturidade-tecnica-carreira.md)
* [Junior vs Senior](./07-comunicacao-e-times/junior-vs-senior.md)
* [Composição de Times](./07-comunicacao-e-times/composicao-de-times.md)
* [Programação em Pares](./07-comunicacao-e-times/programacao-em-pares.md)
* [Prompt Design](./07-comunicacao-e-times/prompt-design.md)

## 08. Estudos de Caso

Aplicações concretas do modelo mental.

* [Estudos de Caso](./08-estudos-de-caso/README.md)
* [Modelagem de Boleto](./08-estudos-de-caso/exemplo-modelagem-boleto.md)
* [Integração por Eventos](./08-estudos-de-caso/exemplo-integracao-eventos.md)

## Mapa Conceitual

```text
Arquitetura como Decisão
  ├── Decisão sob Incerteza
  │   ├── hipótese
  │   ├── reversibilidade
  │   ├── feedback
  │   └── aprendizado
  ├── Complexidade e Trade-offs
  │   ├── simplicidade
  │   ├── abstração prematura
  │   └── carga cognitiva
  ├── Modelagem
  │   ├── comportamento
  │   ├── BDD
  │   ├── FSM
  │   └── parse, don't validate
  ├── Integração
  │   ├── consumidor adapta
  │   ├── source e translation
  │   ├── eventos como fatos
  │   └── contratos versionados
  ├── Arquitetura
  │   ├── acoplamento
  │   ├── ortogonalidade
  │   ├── Conway
  │   ├── observabilidade
  │   └── ADR / C4
  └── Implementação
      ├── código como design
      ├── refactoring
      ├── Demeter
      └── nomeação
```

## Sobre

Mantido por Luciano Yamane como biblioteca pessoal de raciocínio arquitetural, documentação técnica e evolução de sistemas.
