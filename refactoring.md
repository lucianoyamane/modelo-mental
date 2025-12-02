# Refactoring na Prática: Evoluindo Código com Segurança e Clareza

## O que é Refactoring e por que se importa?

> "Refactoring é uma mudança no código para melhorar seu design sem alterar seu comportamento observável." — Martin Fowler

Refactoring é uma prática essencial para manter sistemas saudáveis ao longo do tempo. Trata-se de uma abordagem disciplinada para evoluir o design do software à medida que o entendimento do domínio cresce. É também uma forma de respeitar quem vai ler e manter o código no futuro.

## Quando Refatorar?

* Ao adicionar nova funcionalidade
* Ao corrigir bugs
* Durante revisões de código
* Quando o código “pede” por mudança (bad smells)

## Como faço na prática (experiência pessoal)

Com o tempo, desenvolvi uma abordagem baseada em comportamento e alinhada com as premissas do meu repositório [modelo-mental](https://github.com/lucianoyamane/modelo-mental):

1. **Começo com testes ou comportamentos esperados (BDD)**
2. **Identifico pontos de acoplamento excessivo ou nomes imprecisos**
3. **Uso técnicas como Extract Method, Rename, Introduce Parameter Object, etc.**
4. **Aproveito sessões de Event Storming para alinhar com modelagem**

## Refactoring e arquitetura: aprendizados

* Refactoring ajuda a separar **entidades técnicas** de **entidades de negócio**
* Permite evoluir o design sem grandes reescritas
* Facilita a aplicação de padrões como "source" e "translation"
* Atua como catalisador para o **desacoplamento progressivo**

## Premissas que me ajudam

* **Não modelar regras por antecipação**
* **Comportamento primeiro, implementação depois**
* **O consumidor adapta, não a fonte**

## Exemplos de técnicas na prática

### Replace Conditional with Polymorphism

Transformar condicionais extensos em polimorfismo ajuda a explicitar comportamentos e melhora a extensibilidade.

#### Antes

```java
class CalculadoraDeFrete {
    double calcular(Pedido pedido) {
        if (pedido.tipoEntrega.equals("NORMAL")) {
            return pedido.peso * 1.0;
        } else if (pedido.tipoEntrega.equals("EXPRESSO")) {
            return pedido.peso * 1.5;
        } else {
            return pedido.peso * 2.0;
        }
    }
}
```

#### Depois

```java
interface EstrategiaFrete {
    double calcular(Pedido pedido);
}

class FreteNormal implements EstrategiaFrete {
    public double calcular(Pedido pedido) {
        return pedido.peso * 1.0;
    }
}

class FreteExpresso implements EstrategiaFrete {
    public double calcular(Pedido pedido) {
        return pedido.peso * 1.5;
    }
}

class FreteUrgente implements EstrategiaFrete {
    public double calcular(Pedido pedido) {
        return pedido.peso * 2.0;
    }
}
```

### Extract Method

Isola partes de um código com um nome descritivo, facilitando reutilização e clareza.

```java
// Antes
void printOwing() {
    printBanner();
    double outstanding = 0;
    for (Order o : orders) {
        outstanding += o.getAmount();
    }
    printDetails(outstanding);
}

// Depois
void printOwing() {
    printBanner();
    double outstanding = calculateOutstanding();
    printDetails(outstanding);
}

double calculateOutstanding() {
    double result = 0;
    for (Order o : orders) {
        result += o.getAmount();
    }
    return result;
}
```

### Inline Method

Elimina métodos triviais cujo nome não adiciona clareza.

```java
// Antes
if (getBasePrice() > 1000) ...

// Depois
if (quantity * itemPrice > 1000) ...
```

### Extract Class

Divide classes com muitas responsabilidades, como separar um objeto de endereço de uma entidade cliente.

```java
class Cliente {
    String nome;
    String rua;
    String cidade;
    String cep;
}

// Depois
class Cliente {
    String nome;
    Endereco endereco;
}

class Endereco {
    String rua;
    String cidade;
    String cep;
}
```

### Introduce Parameter Object

Agrupa parâmetros que aparecem juntos em um objeto de domínio.

```java
// Antes
void criarReserva(Date inicio, Date fim) { ... }

// Depois
void criarReserva(Periodo periodo) { ... }

class Periodo {
    Date inicio;
    Date fim;
}
```

Essas técnicas ajudam a tornar o código mais legível, testável e mais alinhado com o modelo de domínio.

## Conclusão

Refatorar é um ato de cuidado com o design e com as pessoas envolvidas no projeto. É uma ponte entre a compreensão tácita adquirida na prática e a intencionalidade arquitetural. Refactoring não é uma etapa final, mas um processo contínuo que fortalece a base de um software sustentável e evolutivo.
