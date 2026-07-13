# Source e Translation

## Contexto

Um conceito recorrente neste repositório é separar a origem autoritativa de informação da forma como cada consumidor interpreta essa informação.

Quando consumidores pressionam a fonte para atender necessidades particulares, o produtor acumula conhecimento que não pertence ao seu contexto. Isso cria acoplamento semântico e dificulta evolução.

## Princípio

O consumidor adapta. A fonte permanece estável.

A fonte publica sua visão do mundo. Cada consumidor traduz essa visão para seu próprio modelo interno.

## Modelo

```text
Source
  |
  v
Contrato publicado
  |
  v
Translation no consumidor
  |
  v
Modelo interno do consumidor
```

## Decisão

Use tradução explícita quando:

* um contexto consome eventos de outro contexto;
* um módulo consulta uma fonte autoritativa;
* uma API externa entra no domínio;
* um modelo técnico precisa virar comportamento de negócio.

## Trade-offs

* Aumenta código de adaptação nos consumidores.
* Preserva estabilidade e autonomia da fonte.
* Reduz negociações de contrato motivadas por casos particulares.
* Evita que modelos externos contaminem o domínio.

## Antipadrões

* Produtor conhecer regras específicas de cada consumidor.
* Evento com campos adicionados apenas para um consumidor isolado.
* DTO externo sendo usado como entidade de domínio.
* Consumidor exigir alteração da fonte para evitar sua própria tradução.

## Relações

* [Arquitetura Fonte da Verdade](./arquitetura-fonte-da-verdade.md)
* [Acoplamento](./acoplamento.md)
* [Parse, Don't Validate](../03-modelagem/parse-dont-validate.md)
