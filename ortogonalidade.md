## Ortogonalidade de sistemas

📚 **Origem**

O termo "ortogonalidade" vem da geometria e descreve a relação entre dois vetores que se encontram em um ângulo reto (90°). Em outras palavras, são **independentes entre si** — a modificação em um vetor não afeta o outro em nenhuma dimensão.

Aplicado ao design de sistemas, esse conceito foi popularizado pelo livro *The Pragmatic Programmer* para expressar a importância de **componentes independentes**, **coesos** e **livres de dependências implícitas**.

---

### 🧠 Princípio

> Um sistema ortogonal é aquele onde **módulos não compartilham responsabilidades que não lhes dizem respeito**, e **a modificação de um não implica mudanças em outros não relacionados**.

---

### 🔍 Aplicações práticas

* **Módulos com responsabilidade única e independente**

  * Um "módulo" pode ser uma classe, componente, serviço, função ou subsistema.
  * Ele deve possuir uma **dimensão de comportamento bem definida** e não conter lógica pertencente a outras dimensões do domínio ou da infraestrutura.
  * Exemplo: um módulo que valida dados de entrada não deve também lidar com persistência ou formatação de resposta.

* **Separação de camadas de tradução**

  * A lógica de transformação entre modelos (ex: DTO ↔ Entidade de domínio ↔ Evento) deve estar **explicitamente isolada**.
  * Essa separação impede que modelos carreguem múltiplas responsabilidades (ex: entidades técnicas acopladas a regras de exposição).

* **Eventos que não exigem conhecimento mútuo**

  * Eventos devem ser **expressões do domínio**, não contratos rígidos de integração.
  * Um produtor ortogonal emite eventos que descrevem *o que ocorreu*, sem saber quem vai consumir ou o que será feito a partir disso.

* **Testabilidade isolada**

  * Módulos ortogonais permitem testes com foco **apenas na responsabilidade em questão**, sem dependências acopladas por conveniência.

* **Alta coesão, baixo acoplamento**

  * Ortogonalidade é uma consequência direta de um design com **coesas unidades de comportamento**, comunicando-se de forma **bem definida e limitada**.

---

### 🚨 Antipadrões que ferem a ortogonalidade

* Módulos com múltiplas razões para mudar.
* "Helper classes" ou "utils" que agregam responsabilidades dispersas.
* Replicação de lógica por ausência de abstrações claras.
* Eventos que dependem da semântica interna de quem os consome.
* Modificações em cadeia como sintoma de acoplamento implícito.

---

### 🎯 Premissas para decisões arquiteturais

* **Ortogonalidade é fundamental para desacoplamento entre partes do sistema.**
* **Design ortogonal reduz risco, facilita testes e melhora a evolução incremental.**
* **Modelos, eventos, serviços e camadas devem expressar uma única perspectiva de responsabilidade.**
