# Exemplo: Integração por Eventos

## Contexto

Um pagamento confirmado pode interessar a faturamento, notificação, conciliação e BI. O produtor não deve conhecer cada consumidor nem publicar comandos específicos para eles.

## Decisão

O contexto de pagamentos publica o fato de negócio:

```text
PagamentoRecebido
```

Cada consumidor traduz o evento para seu próprio modelo.

## Fluxo

```text
Pagamentos
  |
  v
PagamentoRecebido
  |
  +--> Faturamento traduz para emissão de documento
  +--> Notificação traduz para comunicação ao cliente
  +--> BI traduz para projeção analítica
```

## Princípios aplicados

* O consumidor adapta; a fonte permanece estável.
* Eventos representam fatos, não comandos.
* Contratos devem evoluir sem quebrar consumidores.
* A fonte não deve acumular regras de consumidores.
