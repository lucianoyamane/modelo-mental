# Complexidade e Trade-offs

## Contexto

Toda decisão arquitetural altera a distribuição de complexidade do sistema.

Uma solução pode simplificar o produtor e aumentar a responsabilidade dos consumidores. Pode reduzir acoplamento operacional e aumentar complexidade de observabilidade. Pode tornar a escrita mais simples e a leitura mais cara.

O erro comum é tratar complexidade como algo que pode ser eliminado por escolha tecnológica.

## Princípio

Complexidade não desaparece. Ela muda de lugar.

A pergunta arquitetural relevante não é como remover toda complexidade, mas onde ela gera o menor custo para o sistema, para o domínio e para as pessoas que precisam evoluí-lo.

## Implicações

* Decisões devem explicitar quem assume o custo.
* Trade-offs precisam ser discutidos antes da solução parecer óbvia.
* Simplicidade local pode criar complexidade sistêmica.
* Complexidade aceitável é aquela que protege uma propriedade mais importante do sistema.

## Perguntas de decisão

* Que complexidade esta decisão reduz?
* Que complexidade esta decisão cria?
* Quem passa a assumir essa complexidade?
* O contexto justifica esse deslocamento?
* Essa decisão será fácil de reverter se o contexto mudar?

## Relações

Este fundamento sustenta:

* [Arquitetura como Decisão](./arquitetura-como-decisao.md)
* [Simplicidade como Sofisticação](./simplicidade-como-sofisticacao.md)
* [Acoplamento](../04-integracao/acoplamento.md)
* [Heurísticas Arquiteturais](../02-heuristicas/heuristicas-arquiteturais.md)
