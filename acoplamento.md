# Arquitetura Orientada a Eventos, Acoplamento e a Lei de Conway

> "A principal característica de um bom software não é fazer o que faz hoje, mas permitir que continue mudando amanhã."

## Introdução

Toda decisão arquitetural é, na prática, uma decisão sobre **como gerenciar acoplamentos**.

Não existe sistema sem acoplamento. O objetivo da arquitetura nunca foi eliminar dependências, mas **escolher cuidadosamente quais dependências queremos assumir** e quais queremos evitar.

Quanto maior o custo para alterar um sistema, menor é sua capacidade de evoluir. E esse custo é determinado principalmente pelo tipo de acoplamento existente entre seus componentes, seus times e seus domínios.

A Arquitetura Orientada a Eventos (EDA), o Domain-Driven Design (DDD) e a Lei de Conway podem ser vistos como três perspectivas diferentes sobre o mesmo problema:

- Como dividir responsabilidades.
- Como permitir evolução independente.
- Como reduzir o custo das mudanças.

---

# O acoplamento é inevitável

Acoplamento significa que uma parte do sistema depende de outra.

Sem acoplamento não existe sistema.

A pergunta correta não é:

> "Como eliminar o acoplamento?"

Mas sim:

> "Em que exatamente estou me acoplando?"

Alguns acoplamentos são desejáveis.

Outros tornam o software extremamente caro de manter.

## Os cinco tipos de acoplamento

### Acoplamento Operacional

Existe durante a execução.

Um componente depende do outro estar disponível.

Exemplo:

- REST síncrono
- gRPC
- Banco de dados indisponível impede a aplicação

Quanto maior esse acoplamento, menor a resiliência do sistema.

---

### Acoplamento Desenvolvimental

Existe durante a evolução.

Mudanças em um sistema exigem mudanças coordenadas em outro.

Exemplo:

- biblioteca compartilhada
- DTO compartilhado
- contratos que mudam juntos

Esse tipo reduz drasticamente a autonomia das equipes.

---

### Acoplamento Semântico

Dois sistemas compartilham o mesmo significado para determinado conceito.

Mesmo sem compartilhar código, ambos precisam mudar quando a definição muda.

Exemplo:

```
Cliente
Pedido
Pagamento
```

São conceitos compartilhados.

É justamente aqui que o DDD atua.

---

### Acoplamento Funcional

Dois componentes implementam a mesma regra de formas diferentes.

Exemplo:

Dois cálculos diferentes para desconto.

O problema não é duplicação.

O problema é divergência futura.

---

### Acoplamento Incidental

O pior tipo.

Não resolve nenhum problema de negócio.

Apenas surgiu durante a evolução.

Exemplos:

- acessar diretamente tabelas de outro serviço
- consumir campos internos desnecessários
- depender da implementação ao invés da interface

Todo acoplamento incidental gera dívida técnica.

---

# A regra de ouro

Nem todo acoplamento é ruim.

A questão é:

**O quanto aquilo muda?**

Acoplamentos fortes são aceitáveis quando dependem de elementos extremamente estáveis.

Exemplos:

- SQL
- HTTP
- TCP
- JSON

Já componentes em constante evolução exigem acoplamentos fracos.

Exemplos:

- modelo interno
- esquema do banco
- regras de negócio
- detalhes de implementação

Quanto maior a incerteza, menor deve ser o acoplamento.

---

# A Lei de Conway

Melvin Conway observou um comportamento recorrente:

> Organizações projetam sistemas que refletem suas estruturas de comunicação.

Ou seja:

A arquitetura copia a organização.

Não importa o quanto um diagrama esteja bonito.

Se três equipes precisam conversar diariamente para alterar um único fluxo, o software refletirá exatamente essa dependência.

## O contrário também acontece

Arquitetura influencia organizações.

Quando os limites dos domínios são bem definidos, as equipes naturalmente passam a trabalhar nesses mesmos limites.

DDD e Conway caminham juntos.

Primeiro surgem os bounded contexts.

Depois surgem os times responsáveis por eles.

---

# O papel do DDD

DDD não existe apenas para modelar entidades.

Seu maior objetivo é definir fronteiras.

Essas fronteiras permitem responder perguntas importantes:

- Quem é dono deste dado?
- Quem pode alterar esta regra?
- Quem publica este evento?
- Quem apenas consome?

Quando essas fronteiras são claras, o acoplamento diminui naturalmente.

---

# Arquitetura Orientada a Eventos

EDA não elimina acoplamentos.

Ela apenas troca um tipo de dependência por outro.

Ao invés de depender da disponibilidade do produtor, passa-se a depender do contrato da mensagem.

Troca-se:

```
Dependência operacional
```

por

```
Dependência informacional
```

Essa troca costuma ser extremamente vantajosa.

---

## Publicar fatos

Uma boa arquitetura baseada em eventos trabalha com fatos.

Não envia comandos.

Em vez de:

```
Crie um boleto.
```

Publica:

```
PagamentoConfirmado
```

A diferença parece pequena.

Mas muda completamente o grau de acoplamento.

Quem produz apenas conta uma história.

Quem consome decide o que fazer.

Esse princípio reduz dependências entre equipes.

---

# Conte a história inteira

Um evento deve representar um fato completo.

Consumidores não deveriam precisar consultar diversos serviços para entender o que aconteceu.

Um bom evento responde:

- O que aconteceu?
- Quando aconteceu?
- Quem participou?
- Quais informações são necessárias para decisões futuras?

Consumidores devem consumir apenas aquilo que precisam.

Produtores devem publicar uma história suficientemente rica.

---

# Tradução nas bordas

Este é um princípio recorrente no **modelo-mental**.

Nunca permita que modelos externos contaminem seu domínio.

Sempre traduza.

```
Sistema Externo

        ↓

Camada de Tradução

        ↓

Modelo do Domínio
```

O consumidor adapta.

A fonte não.

Isso evita que mudanças externas se propaguem pelo sistema inteiro.

---

# Esconda informação

Interfaces existem para esconder implementação.

Quanto menos conhecimento externo existir sobre um componente, maior sua liberdade para evoluir.

Essa ideia vale para:

- APIs
- eventos
- bancos
- módulos
- bibliotecas

Mudanças internas não deveriam quebrar consumidores.

---

# Feedback rápido ou desastre

Existe uma relação direta entre acoplamento e velocidade de feedback.

Podemos resumir em quatro cenários.

| Acoplamento | Feedback | Resultado |
|-------------|----------|-----------|
| Baixo | Rápido | Cenário ideal |
| Baixo | Lento | Aceitável |
| Alto | Rápido | Sustentável com excelente CI |
| Alto | Lento | Zona de desastre |

A pior combinação possível é:

- forte acoplamento
- feedback lento

É exatamente assim que surgem as famosas **Big Ball of Mud**.

Mudanças passam a ser evitadas.

Deploys tornam-se eventos traumáticos.

O medo substitui a evolução.

---


# TDD revela acoplamentos

Testes difíceis normalmente indicam design difícil.

Quando um teste exige:

- muitos mocks
- dezenas de dependências
- setups enormes

O problema raramente está no teste.

O teste apenas tornou visível um excesso de acoplamento.

Nesse sentido, TDD funciona como um detector de problemas arquiteturais.

---

# EventStorming

Antes de modelar serviços, modele acontecimentos.

EventStorming ajuda a descobrir:

- eventos
- agregados
- comandos
- políticas
- bounded contexts

É frequentemente mais eficiente começar pelos eventos do que pelas entidades.

---

# Governança de eventos

EDA sem documentação rapidamente se torna um novo monólito distribuído.

É importante manter:

- ownership claro
- contratos versionados
- catálogo de eventos
- consumidores conhecidos
- documentação viva

Sem governança, eventos deixam de ser contratos e tornam-se dependências invisíveis.

---

# Relação com o modelo-mental

Este tema reforça diversos princípios já adotados neste repositório:

- consumidor adapta; fonte não;
- tradução nas bordas evita propagação de mudanças;
- eventos representam fatos, não comandos;
- modelar comportamento antes da estrutura;
- esconder detalhes internos reduz acoplamento;
- autonomia depende de fronteiras bem definidas.

EDA não deve ser vista como uma tecnologia.

É uma consequência de um bom desenho de responsabilidades.

---

# Heurísticas

- Não elimine acoplamentos; escolha-os cuidadosamente.
- Acople-se fortemente apenas ao que é estável.
- Esconda implementação.
- Traduza modelos externos na entrada.
- Publique fatos, não comandos.
- Consuma apenas o necessário.
- Produza eventos completos.
- Defina ownership explícito.
- Feedback rápido compensa parte do acoplamento.
- Arquitetura e organização evoluem juntas.

---

---

# Conexões com outros modelos mentais

Este assunto não deve ser entendido de forma isolada. Ele se conecta diretamente com outros princípios arquiteturais.

## Consumidor adapta, fonte não

Um produtor deve publicar fatos sobre seu domínio sem conhecer seus consumidores.

Cada consumidor é responsável por adaptar o evento ao seu próprio modelo.

Isso evita que produtores acumulem conhecimento sobre regras específicas de outros domínios e reduz o acoplamento entre contextos.

A responsabilidade pela tradução sempre pertence ao consumidor.

---

## Tradução nas bordas

Nunca permita que contratos externos contaminem seu domínio.

Toda informação recebida deve passar por uma camada de tradução antes de chegar às regras de negócio.

```
Sistema Externo
        │
        ▼
 Camada de Tradução
        │
        ▼
 Modelo do Domínio
```

Essa estratégia reduz o impacto de mudanças externas e preserva a linguagem ubíqua do domínio.

---

## Eventos representam fatos

Eventos comunicam algo que já aconteceu.

Eles não servem para controlar outros sistemas.

Prefira:

```
PedidoConfirmado
PagamentoRecebido
ClienteCadastrado
```

Ao invés de:

```
CriarBoleto
AtualizarEstoque
EnviarEmail
```

Quando eventos representam fatos, novos consumidores podem surgir sem necessidade de alterar o produtor.

---

## Parse, don't validate

Ao consumir eventos ou APIs externas, transforme imediatamente os dados em tipos válidos do domínio.

Não carregue objetos parcialmente válidos pela aplicação esperando validá-los depois.

```
Mensagem

        ▼

Parsing

        ▼

Objeto de Domínio
```

Isso reduz estados inválidos e simplifica as regras de negócio.

---

## Entidade Técnica × Entidade de Negócio

Eventos normalmente representam conceitos de negócio.

Entidades técnicas existem para suportar a implementação.

Misturar essas responsabilidades faz com que detalhes de infraestrutura vazem para outros contextos.

Sempre que possível, publique eventos utilizando a linguagem do negócio.

---

## Não modele regras por antecipação

EDA facilita adicionar novos consumidores.

Isso significa que não é necessário prever todos os comportamentos futuros.

Publique fatos suficientemente completos e permita que novos casos de uso sejam implementados posteriormente.

O produtor permanece estável enquanto novos consumidores surgem naturalmente.

---

## Bounded Context

Os limites definidos pelo DDD determinam:

- quem publica eventos;
- quem é dono dos dados;
- quais modelos pertencem a cada contexto;
- onde termina uma responsabilidade e começa outra.

Eventos são justamente o mecanismo de comunicação entre esses limites.

---

## Source e Translation

Quando um contexto publica um evento, ele está expondo sua visão do mundo.

Consumidores não devem solicitar alterações nesse contrato para atender necessidades particulares.

Cada contexto traduz o evento recebido para seu próprio modelo interno.

Esse princípio preserva autonomia e reduz negociações entre equipes.

---

# Síntese

Todos esses princípios convergem para uma mesma ideia:

> A arquitetura deve minimizar o impacto das mudanças.

Isso significa:

- proteger o domínio de detalhes externos;
- comunicar fatos em vez de comandos;
- preservar fronteiras claras entre contextos;
- tornar o acoplamento explícito;
- permitir que equipes evoluam de forma independente.

No fim, EDA, DDD, Lei de Conway, tradução nas bordas e adaptação pelo consumidor são diferentes manifestações de um único objetivo: **reduzir o custo da evolução do software**.

# Conclusão

Arquitetura é, essencialmente, gestão de dependências.

O objetivo não é produzir sistemas perfeitos, mas sistemas que permaneçam fáceis de modificar.

A Lei de Conway lembra que a arquitetura reflete a organização.

O DDD ajuda a definir as fronteiras.

A EDA reduz dependências temporais entre essas fronteiras.

Integração Contínua e TDD mantêm essas dependências visíveis.

No fim, a arquitetura não é medida pela quantidade de microsserviços ou eventos, mas pela capacidade do software de continuar evoluindo sem que cada mudança exija uma reorganização completa do sistema ou das equipes.