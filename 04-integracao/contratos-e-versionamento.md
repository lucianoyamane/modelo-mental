# Contratos e Versionamento

## Contexto

Toda integração cria um contrato. Mesmo quando ele não é documentado, ele existe: formato de mensagem, semântica de campos, ordem de eventos, expectativa de disponibilidade, política de erro e regras de compatibilidade.

Contratos implícitos envelhecem mal porque consumidores passam a depender de detalhes que o produtor não sabia estar expondo.

## Princípio

Prefira evoluir contratos a quebrá-los.

Contratos devem proteger autonomia entre contextos, não transformar times em reféns de mudanças coordenadas.

## O que deve ser explicitado

* Dono do contrato.
* Semântica dos campos.
* Garantias de compatibilidade.
* Política de versionamento.
* Estratégia de depreciação.
* Idempotência esperada.
* Tratamento de duplicidade, atraso e reprocessamento.
* Observabilidade mínima para diagnosticar falhas.

## Estratégias de evolução

* Adicionar campos opcionais antes de torná-los obrigatórios.
* Manter consumidores tolerantes a campos desconhecidos.
* Versionar quando a semântica mudar, não apenas quando o schema mudar.
* Publicar eventos novos quando o fato de negócio mudou de significado.
* Depreciar com janela explícita e consumidores conhecidos.

## Riscos

* Versionar cedo demais cria fragmentação.
* Não versionar mudanças semânticas cria bugs silenciosos.
* Compartilhar DTOs entre serviços cria acoplamento desenvolvimental.
* Ignorar idempotência transforma falhas transitórias em inconsistência.

## Relações

* [Eventos Representam Fatos](./eventos-representam-fatos.md)
* [Source e Translation](./source-e-translation.md)
* [CDC e Concorrência](./cdc-e-concorrencia.md)
