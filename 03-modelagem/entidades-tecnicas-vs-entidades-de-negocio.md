# Entidades Técnicas vs Entidades de Negócio

## Contexto

Nem toda entidade persistida, mensagem trafegada ou estrutura operacional é uma entidade de negócio.

Confundir esses níveis faz detalhes de infraestrutura parecerem conceitos do domínio e aumenta o acoplamento entre implementação, integração e regras de negócio.

## Princípio

O domínio deve expressar conceitos de negócio. Estruturas técnicas devem existir para suportar implementação, integração ou operação.

## Diferença

| Tipo | Exemplo | Critério |
|---|---|---|
| Entidade de negócio | Pedido, Pagamento, Fatura | Possui significado e regras na linguagem do domínio |
| Entidade técnica | JobExecution, OutboxMessage, ImportBatch | Suporta processamento, integração ou infraestrutura |
| Modelo externo | DTO, payload, schema CDC | Representa contrato de entrada ou saída |

## Implicações

* Eventos de domínio devem usar linguagem do negócio.
* Tabelas técnicas não devem definir o modelo conceitual.
* DTOs não devem atravessar a aplicação como se fossem domínio.
* Traduções entre esses modelos devem ser explícitas.

## Relações

* [Comportamento Antes da Estrutura](./comportamento-antes-da-estrutura.md)
* [Source e Translation](../04-integracao/source-e-translation.md)
* [Código como Design](../01-fundamentos/codigo-como-design.md)
