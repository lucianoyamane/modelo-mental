# Decisão sob Incerteza

## Contexto

Sistemas de software, equipes e organizações operam em ambientes com incerteza.

Em muitos cenários, a relação entre causa e efeito não pode ser prevista com segurança antes da ação. Mudanças técnicas alteram comportamento, comunicação, operação, expectativas de negócio e a própria forma como o sistema passa a ser compreendido.

Por isso, decisões arquiteturais não devem depender apenas da capacidade de prever corretamente o futuro.

Elas também devem criar condições para aprender rapidamente quando a previsão estiver incompleta, imprecisa ou errada.

## Princípio

Quando não podemos prever com segurança, devemos projetar para aprender.

Boa arquitetura não é apenas tomar decisões melhores. É reduzir o custo de revisar decisões quando o contexto muda ou quando a realidade contradiz nossas hipóteses.

## Sistemas complexos

Em sistemas complexos:

* relações de causa e efeito podem ficar claras apenas em retrospecto;
* intervenções alteram o próprio sistema;
* planos detalhados de longo prazo perdem validade conforme o contexto muda;
* aprendizado empírico tende a ser mais confiável do que previsão excessiva.

Isso não significa abandonar planejamento.

Significa ajustar o nível de confiança depositado no plano.

Quanto maior a incerteza, menor deve ser a confiança em previsões detalhadas e maior deve ser a capacidade de observar, aprender e corrigir direção.

## Modelo de raciocínio

```text
Contexto
    ↓
Problema
    ↓
Hipótese
    ↓
Decisão
    ↓
Mudança pequena e reversível
    ↓
Observação
    ↓
Feedback
    ↓
Aprendizado
    ↓
Nova decisão
```

Esse fluxo não é um processo rígido.

Ele representa uma forma de raciocinar em ambientes nos quais a previsão é limitada.

## Sondar, observar e responder

Diante de alta incerteza, a abordagem mais segura costuma ser:

```text
Sondar
  ↓
Observar
  ↓
Responder
```

Sondar significa executar uma intervenção pequena o suficiente para limitar o impacto.

Observar significa medir as consequências reais da mudança.

Responder significa ajustar a decisão a partir do que foi aprendido.

## Reduzir o custo de estar errado

Em vez de perguntar apenas:

> Como aumentamos a chance de acertar?

Também devemos perguntar:

> Como reduzimos o custo de estar errado?

Essa mudança de perspectiva conecta arquitetura, engenharia e operação.

Algumas práticas reduzem o custo do erro porque tornam a experimentação mais barata e o aprendizado mais rápido:

* controle de versão;
* testes automatizados;
* Continuous Delivery;
* rollback;
* feature flags;
* deploy progressivo;
* observabilidade;
* mudanças incrementais;
* contratos evolutivos.

Essas práticas não são respostas universais.

Elas são mecanismos para diminuir o tamanho da aposta, reduzir o blast radius e acelerar feedback.

## Reversibilidade

Reversibilidade é uma propriedade relevante de decisões arquiteturais.

Uma pergunta importante é:

> Quão caro é desfazer esta decisão?

Sob incerteza, decisões reversíveis tendem a ser preferíveis porque permitem aprendizado com menor risco.

Quanto mais difícil for reverter uma decisão, mais evidência ela exige antes de ser tomada.

Isso não elimina decisões difíceis de reverter. Algumas precisam ser feitas.

O ponto é tornar explícito o custo da reversão.

## Hipótese antes da mudança

Uma mudança sem consequência esperada dificulta aprendizado.

Antes de uma decisão relevante, procure explicitar:

* o que acreditamos que acontecerá;
* por que acreditamos nisso;
* como saberemos se aconteceu;
* qual evidência poderá invalidar nossa hipótese.

Sem consequência esperada, uma decisão não pode ser avaliada.

Sem observação, uma consequência não pode ser comparada.

Sem comparação, não há aprendizado.

## Velocidade e segurança

Velocidade e segurança podem ser trade-offs reais.

Mas antes de aceitar esse conflito como natural, vale investigar se ele é inerente ao problema ou consequência do processo atual.

Uma organização pode acreditar que liberar software com segurança exige lentidão quando, na prática, seu processo de entrega tornou o erro caro demais.

Melhorias de engenharia podem aumentar simultaneamente:

* frequência de deploy;
* confiabilidade;
* capacidade de rollback;
* qualidade do feedback;
* segurança operacional.

O objetivo não é negar trade-offs.

É evitar tratá-los como inevitáveis antes de entender suas causas.

## Segurança para falhar

Seguro para falhar não significa permissão para agir sem cuidado.

Significa criar condições para que pessoas possam formular hipóteses, tentar mudanças pequenas, estar erradas sem culpabilização e aprender com resultados inesperados.

A capacidade técnica de limitar danos é tão importante quanto a segurança psicológica.

```text
Segurança para falhar
        =
Cultura
        +
Engenharia
```

## Heurísticas

* Quando não podemos prever com segurança, devemos projetar para aprender.
* Quanto maior a incerteza, menor deveria ser o tamanho da decisão.
* Sob incerteza, prefira decisões reversíveis.
* Quanto mais difícil for reverter uma decisão, mais evidência ela exige.
* Reduza o custo de estar errado.
* Sem consequência esperada, uma decisão não pode ser avaliada.
* Feedback rápido reduz o custo da incerteza.
* Observabilidade fecha o ciclo de decisão.
* Antes de aceitar um trade-off, investigue se ele é inerente ao problema ou consequência do processo atual.
* Grandes mudanças aumentam o risco e reduzem a capacidade de aprender.
* Mude a forma como você muda.

## Relações

* [Arquitetura como Decisão](./arquitetura-como-decisao.md)
* [Complexidade e Trade-offs](./complexidade-e-trade-offs.md)
* [Abstração Prematura](./abstracao-prematura.md)
* [Heurísticas Arquiteturais](../02-heuristicas/heuristicas-arquiteturais.md)
* [BDD](../03-modelagem/bdd.md)
* [Observabilidade](../05-arquitetura/observabilidade.md)
* [ADR](../05-arquitetura/adr.md)
