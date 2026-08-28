# ADR: Architecture Decision Record

## Contexto

Este repositório defende que decisões explícitas envelhecem melhor que decisões implícitas.

ADRs existem para registrar contexto, alternativas, decisão e consequências. O objetivo não é burocratizar arquitetura, mas preservar raciocínio para que decisões possam ser entendidas e revisitadas.

Em ambientes de incerteza, uma decisão arquitetural também carrega uma hipótese: acreditamos que determinada escolha produzirá determinada consequência.

Registrar essa hipótese torna possível observar resultados, aprender e revisar a decisão quando necessário.

## Quando usar

Use ADR quando a decisão:

* altera fronteiras entre módulos, serviços ou times;
* cria ou muda contratos de integração;
* introduz tecnologia, padrão ou dependência relevante;
* assume trade-offs significativos;
* será difícil de compreender no futuro apenas olhando o código.

## Template resumido

```markdown
# ADR: <titulo>

## Status

Proposto | Aceito | Substituído | Revogado

## Contexto

Qual problema estamos resolvendo?
Quais restrições existem?

## Decisão

O que foi decidido?

## Hipótese

O que acreditamos que esta decisão irá melhorar?

Como saberemos se isso aconteceu?

## Alternativas consideradas

Quais opções foram avaliadas?

## Consequências

Quais benefícios, custos, riscos e trade-offs foram aceitos?

## Critérios de revisão

Em que condições esta decisão deve ser reavaliada?

Que evidência indicaria que a hipótese da decisão estava errada ou deixou de ser válida?
```

## Relações

* [Arquitetura como Decisão](../01-fundamentos/arquitetura-como-decisao.md)
* [Decisão sob Incerteza](../01-fundamentos/decisao-sob-incerteza.md)
* [Heurísticas Arquiteturais](../02-heuristicas/heuristicas-arquiteturais.md)
