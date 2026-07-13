# Premissa de Desenvolvimento: Abstração Prematura e o Custo das Más Abstrações

> "Code duplication is far cheaper in terms of technical debt than a wrong abstraction."  
> — *Sandi Metz*

## 🎯 Propósito

Este documento tem como objetivo registrar uma premissa fundamental que adoto no desenvolvimento de software: **evitar abstrações prematuras**. Essa prática tem impacto direto na manutenibilidade, na evolução e na simplicidade dos sistemas.

O conteúdo aqui apresentado é inspirado e fortemente baseado no vídeo:  
👉 [Premature Abstraction — YouTube](https://www.youtube.com/watch?v=1M5Jn86apeM)

---

## 🏗️ A Analogia da Casa

Imagine que você está construindo uma casa. Naturalmente, você planeja:

- Uma cozinha 🍳
- Um banheiro 🚽
- Um quarto 🛏️
- Uma sala 🛋️

Então, surge aquele pensamento clássico:  
*"E se no futuro precisarmos de um segundo quarto? E se for necessário mais um banheiro? Melhor já deixar um espaço reservado para qualquer coisa..."*

🔧 Resultado:

- O custo da obra sobe desnecessariamente.
- Áreas construídas sem necessidade real precisam de manutenção.
- O espaço reservado foi maior do que o necessário.

No final, você percebe que:

- O segundo banheiro **nunca foi usado**, mas gera custo.
- O espaço reservado ficou subutilizado.
- O custo e a complexidade aumentaram sem entregar valor.

Essa é exatamente a metáfora para a **abstração prematura no software**.

---

## ⚠️ O Problema da Abstração Prematura

### 🚩 O que é?

Criar estruturas, padrões, interfaces ou generalizações **antes que a necessidade real exista**.

### 🔥 Sintomas comuns:

- Implementar interfaces “porque talvez um dia mude”.
- Criar padrões complexos como Strategy, Factory, Observer... sem necessidade atual.
- Microserviços, filas, brokers, eventos, camadas e mais camadas... **antes mesmo de entregar a primeira feature.**

### 💣 O custo oculto:

- 📈 Aumento de complexidade.
- 🧠 Maior carga cognitiva para entender o sistema.
- 🔧 Mais difícil de alterar e evoluir.
- 🐌 Diminuição da velocidade de desenvolvimento.
- 😨 Medo constante de quebrar outras partes do sistema.

---

## 💡 Por que a duplicação, às vezes, é melhor?

- Código duplicado é **local**, fácil de entender, fácil de alterar.
- Abstrações ruins são **globais**, difíceis de alterar, quebram em cascata.
- Muitas vezes, aquilo que parece similar no início, se mostra diferente no futuro.
- **A duplicação permite que o padrão real emerja ao longo do tempo.**

---

## 🆚 DRY vs. YAGNI

| Princípio | Descrição | Quando aplicar |
|------------|-----------|----------------|
| **DRY** (*Don't Repeat Yourself*) | Evite duplicação de **conhecimento**, não necessariamente de código literal. | Somente quando for claro que os comportamentos são realmente equivalentes e estáveis. |
| **YAGNI** (*You Ain't Gonna Need It*) | Não implemente nada que não seja necessário **agora**. | Sempre que surgir a tentação de generalizar ou prever necessidades futuras sem evidência. |

---

## ✔️ Princípios que sigo

- 🛑 **Evito abstrações até que a duplicação grite de dor.**  
- 🔍 Prefiro **clareza sobre sofisticação**.  
- 🔄 **Refatoro quando há padrões maduros**, não por antecipação.  
- 🪪 **Interfaces, padrões e generalizações surgem como consequência da evolução**, não como ponto de partida.  
- 🚦 Sempre me pergunto:  
  > "Isso resolve o problema de hoje ou o problema que *acho* que terei daqui 6 meses?"

---

## 📜 Frases para lembrar

> 🏗️ **"Construa para o hoje. Refatore para o amanhã."**  
> 🔥 **"O pior código não é o duplicado. É o genérico demais sem necessidade."**  
> 🧠 **"É mais barato e seguro manter duplicação do que lidar com uma abstração errada."**  
> 💡 **"Se você não consegue descrever o problema claramente, a solução será acidental."**

---

## 📺 Referência Original

**Premature Abstraction – YouTube**  
▶️ [https://www.youtube.com/watch?v=1M5Jn86apeM](https://www.youtube.com/watch?v=1M5Jn86apeM)

---

## 🚀 Conclusão

A prática de evitar abstrações prematuras não significa ignorar boas práticas, mas sim respeitar o tempo certo de cada decisão de design. A simplicidade é uma virtude que impulsiona a manutenibilidade, a agilidade e a qualidade do software.

---
