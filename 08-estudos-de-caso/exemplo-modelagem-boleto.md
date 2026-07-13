# Exemplo: Modelagem de Boleto

## Contexto

Boletos podem permanecer indefinidamente em estado intermediário quando o fluxo não define estados finais e eventos de encerramento.

## Decisão de modelagem

O boleto deve terminar em um dos estados finais:

* `PAGO`
* `EXPIRADO`
* `CANCELADO`

## Eventos relevantes

* `BoletoEmitido`
* `PagamentoRecebido`
* `BoletoExpirado`
* `BoletoCancelado`

## Regra de vencimento

A cada ciclo de verificação:

* se `hoje > dataVencimento`;
* e o boleto ainda está `EMITIDO`;
* então gerar `BoletoExpirado`.

## Princípios aplicados

* Comportamento revela conhecimento.
* Eventos representam fatos.
* Estados finais devem ser explícitos.
* Não confundir estado com evento.
