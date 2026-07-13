
# 📘 Guia Completo de Prompt Design com IA Generativa

## ✨ Introdução

Este guia foi criado para ajudar você a escrever prompts mais claros, eficazes, éticos e adaptáveis para ferramentas de IA generativa. Ele cobre desde estruturas básicas até estratégias avançadas como multimodalidade, tom, estilo, encadeamento, agentes e uso responsável.

---

## 🧠 O que é Prompt Design?

Prompt design é a prática de criar instruções precisas e contextuais para que uma ferramenta de IA gere resultados úteis. Bons prompts reduzem o tempo de iteração e melhoram a qualidade da saída.

---

## 🧱 Estrutura TCREI para Criar Prompts

| Sigla | Elemento    | Explicação                                                 |
| ----- | ----------- | ---------------------------------------------------------- |
| T     | Tarefa      | O que você quer que a IA faça                              |
| C     | Contexto    | Situação ou detalhes relevantes para a tarefa              |
| R     | Referência  | Exemplo de formato ou estilo esperado (opcional, mas útil) |
| E     | Expectativa | O que você quer receber da IA como resultado               |
| I     | Iteração    | Como pretende revisar ou ajustar a resposta                |

---

## Detalhamento do TCREI

### T - Tarefa

Declare objetivamente o resultado esperado. Use verbos fortes como analisar, criar, resumir, comparar ou revisar. Quando fizer sentido, indique a persona técnica esperada.

### C - Contexto

Forneça cenário, público, restrições, domínio e finalidade. Contexto rico reduz ambiguidade, mas contexto sem foco dispersa a resposta.

### R - Referência

Inclua exemplos de formato, estilo, estrutura ou critérios. Referências próximas do resultado esperado são mais úteis do que descrições genéricas como "um bom artigo".

### E - Expectativa

Defina formato, tamanho, nível técnico, tom, critérios de aceite e uso final. Sem expectativa clara, a IA tende a preencher lacunas com suposições.

### I - Iteração

Planeje ciclos de refinamento. Peça comparação de alternativas, revisão por critérios e ajustes incrementais quando a tarefa for complexa.

---

## 🏗️ Estrutura Universal de Prompt

```xml
<task>
Descreva claramente o que a IA deve fazer.
</task>
<context>
Inclua informações específicas e relevantes sobre a situação.
</context>
<references>
Adicione exemplos ou estilos que deseja seguir.
</references>
<format>
Especifique o formato da resposta (lista, markdown, etc.).
</format>
<criteria>
Inclua limitações, preferências e filtros.
</criteria>
<iteration>
Peça à IA para oferecer sugestões de melhoria ou ajuste.
</iteration>
```

---

## 🔁 Estratégias de Iteração

1. **Revisar a Estrutura:** Torne a tarefa mais clara e específica.
2. **Dividir em Etapas:** Separe a tarefa em prompts menores.
3. **Reformular a Linguagem:** Use outra abordagem ou analogia.
4. **Adicionar Restrições:** Limite tempo, escopo, estilo, conteúdo ou formato.

---

## ✍️ Constraints (Restrições) em Prompts

Limites explícitos para controlar melhor a saída da IA.

Exemplos:
- Formato: “Use bullet points.”
- Tamanho: “No máximo 100 palavras.”
- Estilo: “Evite linguagem técnica.”
- Conteúdo: “Apenas receitas veganas.”

Benefícios:
- Melhora foco.
- Reduz ambiguidades.
- Gera respostas mais relevantes.

---

## 📸 Prompt Multimodal

Combinação de diferentes mídias em um único prompt (ex.: texto + imagem).

Estrutura:
- Tarefa: O que gerar e como usar cada mídia.
- Contexto: Detalhes para uso correto.
- Referências: Exemplos, imagens ou áudios.
- Critérios: Restrições específicas.
- Iteração: Solicite ajustes em cada componente.

---

## 🎯 Tom e Estilo

A IA ajusta o tom com base no público, sinais linguísticos e referências.

Dicas:
- Especifique o tom: “Otimista e informal, como um amigo.”
- Evite termos vagos: Use “humor sutil” em vez de só “engraçado”.
- Adicione restrições: “Evite jargões técnicos.”

---

## 🧠 Large Context Window

Permite que a IA processe mais informações de uma vez:
- Conversas longas com histórico completo.
- Documentos grandes e detalhados em um único input.

Dica: Clareza continua fundamental mesmo com mais contexto.

---

## 📚 Chain-of-Density

Técnica para gerar resumos densos e informativos:
1. Resumo básico.
2. Identificar informações faltantes.
3. Reescrever adicionando dados importantes.
4. Repetir até o resumo estar completo.

---

## ⚙️ Ajuste Fino: Temperatura, Top-k, Top-p

- Temperatura: Baixa = previsível, Alta = criativo.
- Top-k: Limita número de tokens considerados.
- Top-p: Limita por soma de probabilidade.

Use para equilibrar criatividade e precisão.

---

## 🔗 Encadeamento de Prompt

Divida tarefas em partes menores e conectadas.

Exemplo:
1. Gere esboço de curso.
2. Expanda item em parágrafo.
3. Crie quiz com base no parágrafo.

Inclui:
- **Chain-of-Thought**: Peça raciocínio passo a passo.
- **Tree-of-Thought**: Explore várias soluções e escolha.

---

## 🧩 Meta-Prompting

Usar a IA para criar ou refinar o próprio prompt.

Estratégias:
- Geração direta: “Gere um prompt para carta de oferta.”
- Modelo: “Crie um modelo de prompt para planejamento de viagem.”
- Encadeamento: Subdivida a criação em subprompts.
- Remixagem: Combine vários prompts em um só.
- Troca de estilo: Mude tom e humor do prompt.

---

## 🤖 Agentes de IA

Crie personas especializadas para ajudar em tarefas.

Como criar:
- Defina persona: “Aja como consultor de negócios.”
- Dê contexto: “Quero melhorar minha negociação.”
- Tipo de conversa: “Faça simulações e dê feedback.”
- Frase de parada: “I'm finished.”
- Conclusões: “Forneça um resumo final.”

Exemplos de uso:
- Coach de negociação.
- Editor literário.
- Tutor de idiomas.
- Redator de subsídio.

---

## ✅ Conclusão

Prompts bem desenhados combinam clareza, técnica e responsabilidade. Com boas práticas, a IA se torna uma poderosa aliada na sua produtividade.
