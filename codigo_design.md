# O Código é o Design: A Teoria por Trás das Abstrações

> "O código-fonte é o design do software." – Jack W. Reeves

## Introdução

Em outras engenharias, o design é um insumo que antecede a fabricação. Em software, o design é o próprio produto: o código-fonte. Isso implica que, ao codificar, estamos continuamente projetando. Essa visão, longe de ser meramente filosófica, tem implicações práticas profundas sobre como pensamos evolução, legibilidade, abstração e acoplamento.

Este artigo estrutura um modelo mental que conecta conceitos como "código como design", "teoria do programa" e "refatorar como comunicar intenção".

---

## 1. Codificar é projetar

A separação entre design e implementação é ilusória. No fluxo de trabalho moderno, o compilador e o pipeline de build exercem o papel de manufatura. O que entregamos é o próprio design executável.

### Implicação

* Não existe "escrever código sem pensar em design".
* Testes, depuração e refatoramento são partes essenciais do processo de design.
* Arquitetura não é um artefato estático, mas um fluxo de decisões refletidas no código.

---

## 2. Para modificar, é preciso compreender

Peter Naur propôs que o ato de programar consiste na construção de uma teoria sobre o sistema. Esta teoria é um modelo mental formado pelas pessoas que escrevem e mantêm o software.

> "Um sistema é compreendido quando é possível modificá-lo corretamente."

Essa teoria não está no código nem na documentação. Ela vive na mente dos desenvolvedores.

### Implicação

* Projetar bem é facilitar a construção de uma teoria correta por quem lê o código.
* Nominar bem importa. Uma função nomeada corretamente comunica intenção.
* Cada abstração é uma "caixa mental". Seu nome define seu papel na teoria do leitor.

---

## 3. Refatorar é tornar a teoria visível

Refatorar é o ato de explicitar melhor a teoria que já existe na cabeça do desenvolvedor. Ao extrair uma função, criamos um novo bloco conceitual. O nome escolhido comunica ao leitor qual parte da teoria ele pode isolar mentalmente.

### Exemplo

```java
// Antes
doWork();

// Depois
if (user.isEligible()) {
    grantAccess(user);
}
```

A nomeação "isEligible" e "grantAccess" orienta o leitor sobre a intenção de cada bloco, mesmo sem ler sua implementação interna.

---

## 4. O custo da mudança é o custo do acoplamento

Segundo a "Equivalência de Constantine":

> Custo do Software ≈ Custo das Mudanças ≈ Quantidade de Acoplamento

Reduzir acoplamento é reduzir o custo de alteração. Essa propriedade está diretamente relacionada à ortogonalidade: quanto mais ortogonais são os componentes do sistema, menor o impacto cruzado entre eles. Ortogonalidade permite que decisões locais não reverberem globalmente, tornando o design mais previsível e evolutivo.

### Conexão com o modelo-mental

* Usar "translation" e "source" para desacoplar regras.
* Isolar "entidades técnicas" de "entidades de negócio" para proteger os limites.
* Evitar que eventos carreguem semântica compartilhada desnecessária.

---

## Conclusão

Projetar é codificar. Refatorar é comunicar. Compreender é criar teoria. Um bom design é aquele que reduz o custo da mudança, não aquele que antecipa todas as possibilidades.

Esse modelo mental orienta decisões concretas: ao nomear, ao extrair, ao modularizar e ao versionar.

> O código não é apenas uma instrução para a máquina. É um meio de expressar nossa teoria do sistema para outros humanos.

---

**Relacionado:**

* [modelo-mental/parse-dont-validate](https://github.com/lucianoyamane/modelo-mental/blob/main/parse-dont-validate.md)
* [modelo-mental/source-translation.md](https://github.com/lucianoyamane/modelo-mental/blob/main/source-translation.md)
* [modelo-mental/nomear-com-intencao.md](https://github.com/lucianoyamane/modelo-mental/blob/main/nomear-com-intencao.md)
