# Observabilidade

## Contexto

Arquiteturas distribuídas trocam simplicidade local por complexidade operacional. Mensageria, CDC, consistência eventual, retries e execução assíncrona reduzem alguns acoplamentos, mas tornam o comportamento do sistema mais difícil de enxergar.

## Princípio

Observabilidade é parte da decisão arquitetural, não um acessório operacional.

Se uma decisão torna o sistema mais distribuído, assíncrono ou resiliente, ela também deve definir como será observada em produção.

## Sinais mínimos

* Logs estruturados com correlação.
* Métricas de latência, throughput, erro e saturação.
* Traces distribuídos para fluxos entre serviços.
* Métricas de consumidores, filas, lag e reprocessamento.
* Alertas baseados em sintomas relevantes para o negócio.

## Perguntas de decisão

* Como saberemos que o fluxo falhou?
* Como rastrear uma transação entre contextos?
* Como medir atraso, duplicidade e reprocessamento?
* Quais sinais indicam degradação antes de indisponibilidade?
* O time que opera o sistema entende os sinais produzidos?

## Relações

* [Manifesto Reativo](./manifesto-reativo.md)
* [CDC e Concorrência](../04-integracao/cdc-e-concorrencia.md)
* [Contratos e Versionamento](../04-integracao/contratos-e-versionamento.md)
