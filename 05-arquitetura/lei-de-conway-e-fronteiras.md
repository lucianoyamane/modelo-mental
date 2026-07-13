# Lei de Conway e Fronteiras

## Contexto

A arquitetura de um sistema tende a refletir a estrutura de comunicação da organização que o constrói.

Quando três equipes precisam se coordenar diariamente para alterar um fluxo, o software normalmente carrega a mesma dependência em seus módulos, serviços e contratos.

## Princípio

Arquitetura e organização evoluem juntas.

Fronteiras técnicas só se sustentam quando também fazem sentido para ownership, comunicação e tomada de decisão.

## Implicações

* Bounded contexts ajudam a definir ownership.
* Times devem conseguir evoluir seus contextos sem coordenação excessiva.
* Integrações devem explicitar contratos entre fronteiras.
* Acoplamento entre times frequentemente revela acoplamento no software.
* Separar serviços sem separar responsabilidades apenas distribui o problema.

## Perguntas de decisão

* Quem é dono deste dado?
* Quem pode alterar esta regra?
* Quem publica este evento?
* Quem apenas consome?
* Quantas equipes precisam coordenar para mudar este comportamento?

## Relações

* [Acoplamento](../04-integracao/acoplamento.md)
* [Source e Translation](../04-integracao/source-e-translation.md)
* [Ortogonalidade](./ortogonalidade.md)
