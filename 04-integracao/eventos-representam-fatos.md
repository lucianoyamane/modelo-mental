# Eventos Representam Fatos

## Contexto

Eventos mal modelados viram comandos disfarçados. Quando isso acontece, o produtor passa a controlar o comportamento de consumidores e a arquitetura orientada a eventos perde boa parte do desacoplamento prometido.

## Princípio

Eventos comunicam algo que aconteceu. Eles não devem ordenar que outro sistema faça algo.

Prefira eventos no passado, com significado de negócio:

```text
PedidoConfirmado
PagamentoRecebido
ClienteCadastrado
```

Evite comandos disfarçados:

```text
CriarBoleto
AtualizarEstoque
EnviarEmail
```

## Um bom evento responde

* O que aconteceu?
* Quando aconteceu?
* Quem participou?
* Qual contexto publicou o fato?
* Quais informações são necessárias para decisões futuras?

## Trade-offs

* Eventos ricos reduzem chamadas adicionais dos consumidores.
* Eventos pobres criam acoplamento operacional indireto.
* Eventos genéricos demais perdem semântica de negócio.
* Eventos específicos demais podem revelar detalhes internos do produtor.

## Relações

* [Acoplamento](./acoplamento.md)
* [Contratos e Versionamento](./contratos-e-versionamento.md)
* [Comportamento Antes da Estrutura](../03-modelagem/comportamento-antes-da-estrutura.md)
