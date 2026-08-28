# Heurísticas Arquiteturais

> Heurísticas não são regras.
>
> São atalhos mentais que ajudam na tomada de decisão quando não existe uma resposta única.
>
> Devem ser questionadas sempre que o contexto justificar.

---

# Sobre o problema

* Nunca proponha uma solução antes de entender o problema.
* Respostas sem perguntas costumam gerar complexidade desnecessária.
* Toda solução deve justificar claramente qual problema resolve.
* O contexto vale mais do que a tecnologia.

---

# Sobre complexidade

* Complexidade não desaparece. Ela apenas muda de lugar.
* Simplificar um componente normalmente aumenta a responsabilidade de outro.
* Reduza a carga cognitiva antes de otimizar performance.
* Toda abstração possui um custo.
* Se uma abstração exige mais explicação do que o problema original, provavelmente ela não vale a pena.

---

# Sobre modelagem

* Modele conhecimento observado, não possibilidades futuras.
* Não antecipe regras de negócio.
* O comportamento revela o modelo.
* O nome de um conceito deve refletir o domínio, não a implementação.
* Toda modelagem deve facilitar mudanças futuras, não dificultá-las.

---

# Sobre integração

* O consumidor adapta; a fonte permanece estável.
* Traduza modelos nas fronteiras, não no núcleo do domínio.
* Toda integração cria um contrato.
* Contratos devem minimizar dependências entre contextos.
* Prefira evoluir contratos a quebrá-los.

---

# Sobre decisões

* Não existe arquitetura perfeita; existe arquitetura adequada.
* Toda decisão possui trade-offs.
* Decisões explícitas envelhecem melhor do que decisões implícitas.
* Registre o motivo da decisão, não apenas a decisão.
* Sem consequência esperada, uma decisão não pode ser avaliada.
* Quando o contexto muda, reavalie as decisões.

---

# Sobre incerteza e aprendizado

* Quando não podemos prever com segurança, devemos projetar para aprender.
* Quanto maior a incerteza, menor deveria ser o tamanho da decisão.
* Sob incerteza, prefira decisões reversíveis.
* Quanto mais difícil for reverter uma decisão, mais evidência ela exige.
* Reduza o custo de estar errado.
* Feedback rápido reduz o custo da incerteza.
* Observabilidade fecha o ciclo de decisão.
* Grandes mudanças aumentam o risco e reduzem a capacidade de aprender.

---

# Sobre simplicidade

* Simplicidade é uma característica arquitetural.
* O código mais fácil de entender costuma ser o mais barato de manter.
* Faça o simples funcionar antes de torná-lo genérico.
* Generalize somente quando houver evidências.
* Evite otimizações especulativas.

---

# Sobre responsabilidades

* Quem possui o contexto deve tomar a decisão.
* Centralizar conhecimento cria gargalos.
* Distribua responsabilidades, não apenas componentes.
* O sistema deve depender o mínimo possível de especialistas.

---

# Sobre documentação

* Documente decisões, não apenas estruturas.
* Todo documento deve responder uma pergunta específica.
* Diagramas existem para facilitar entendimento, não para impressionar.
* Atualize a documentação quando a decisão mudar, não apenas quando o código mudar.

---

# Sobre evolução

* Arquitetura é uma atividade contínua.
* Sistemas evoluem melhor quando as decisões são pequenas e reversíveis.
* Prefira mudanças incrementais a grandes reescritas.
* Antes de aceitar um trade-off, investigue se ele é inerente ao problema ou consequência do processo atual.
* Mude a forma como você muda.
* A melhor arquitetura é aquela que facilita a próxima mudança.

---

# Sobre o papel do arquiteto

* O arquiteto melhora decisões, não centraliza poder.
* Explique o "porquê" antes do "como".
* Ensinar vale mais do que responder.
* O objetivo não é ser a pessoa mais inteligente da sala, mas aumentar a inteligência coletiva.
* Uma boa arquitetura continua evoluindo mesmo quando o arquiteto não está presente.

---

# Heurística final

Antes de tomar qualquer decisão arquitetural, pergunte:

* Estamos resolvendo um problema real?
* Esta decisão reduz ou redistribui a complexidade?
* Quem assumirá o custo dessa decisão?
* O contexto justifica essa escolha?
* Os trade-offs estão explícitos?
* Qual hipótese esta decisão assume?
* Como observaremos suas consequências?
* Quanto custa estar errado?
* Esta decisão facilita ou dificulta a evolução futura do sistema?
