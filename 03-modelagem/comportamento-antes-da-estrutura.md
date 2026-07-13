# Comportamento Antes da Estrutura

## Contexto

Modelos frágeis costumam nascer quando começamos por tabelas, classes, endpoints ou tecnologias antes de compreender o comportamento esperado do sistema.

No modelo mental deste repositório, comportamento é a evidência primária do domínio.

## Princípio

Comportamento revela conhecimento.

Antes de definir a estrutura, é preciso entender o que o sistema deve permitir, impedir, transformar, registrar e comunicar.

## Aplicações

* Em BDD, cenários descrevem o que deve acontecer, não como será implementado.
* Em máquinas de estado, transições tornam explícito quais eventos mudam o estado do domínio.
* Em eventos, fatos do negócio são mais estáveis que comandos técnicos.
* Em refatoração, nomes melhores tornam visível a intenção que já existia de forma implícita.

## Perguntas de modelagem

* Qual comportamento precisa ser protegido?
* Que evento ou decisão de negócio altera esse comportamento?
* A regra já existe no domínio ou está sendo antecipada?
* O modelo expressa linguagem de negócio ou detalhes de implementação?
* O comportamento continua compreensível sem conhecer a infraestrutura?

## Relações

* [BDD](./bdd.md)
* [Máquinas de Estado](./finite-state-machine.md)
* [Eventos Representam Fatos](../04-integracao/eventos-representam-fatos.md)
* [Refactoring](../06-implementacao/refactoring.md)
