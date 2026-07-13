# C4 Model

## Contexto

Diagramas arquiteturais só ajudam quando reduzem carga cognitiva. O C4 Model é útil porque separa níveis de abstração e evita misturar contexto, containers, componentes e código no mesmo desenho.

## Princípio

Diagramas existem para facilitar decisão e entendimento compartilhado, não para impressionar.

## Níveis

| Nível | Pergunta respondida |
|---|---|
| Contexto | Quem usa o sistema e com quais sistemas ele se relaciona? |
| Containers | Quais aplicações, bancos, filas e serviços compõem a solução? |
| Componentes | Como um container relevante é dividido internamente? |
| Código | Quais classes ou estruturas implementam um componente? |

## Quando usar

* Onboarding técnico.
* Discussão de fronteiras.
* Avaliação de integração.
* Registro de decisão arquitetural.
* Comunicação com stakeholders técnicos e não técnicos.

## Cuidados

* Não misture níveis no mesmo diagrama.
* Não detalhe o que não ajuda a decisão.
* Atualize quando a decisão mudar.
* Complemente diagramas com ADRs quando houver trade-offs relevantes.

## Relações

* [ADR](./adr.md)
* [Arquitetura como Decisão](../01-fundamentos/arquitetura-como-decisao.md)
* [Ortogonalidade](./ortogonalidade.md)
