
# 📘 Guia Avançado de Prompt Design com TCREI

## ✨ Introdução

Este guia avançado oferece um aprofundamento prático sobre como atuar em relação a cada elemento do framework **TCREI** no design de prompts para IA generativa. A ideia é fornecer nuances e orientações práticas para você construir prompts mais claros, eficazes e éticos.

---

## 🧱 Framework TCREI - Detalhamento

### 🟣 **T - Tarefa**

A **Tarefa** define claramente o que você quer que a IA faça.  
**Como atuar:**  
✅ Declare de forma objetiva e específica o que você espera (ex.: "Gere um resumo técnico", "Crie um esboço em Markdown").  
✅ Indique a persona: peça que a IA atue como um especialista quando relevante (ex.: "Aja como um editor literário").  
✅ Evite ambiguidade — diga o resultado esperado, não só a ação.

**Nuances:**  
- Um verbo forte na tarefa ajuda: “Analise”, “Crie”, “Resuma”.  
- Se o objetivo for criativo, abra espaço para mais liberdade no verbo (ex.: "Imagine", "Desenvolva").

---

### 🟣 **C - Contexto**

O **Contexto** fornece o cenário para a tarefa.  
**Como atuar:**  
✅ Explique o ambiente, o público-alvo, limitações práticas, tom esperado.  
✅ Dê detalhes que moldem a resposta: “Documento será lido por executivos”, “Destinado a alunos do ensino médio”.  
✅ Contextos ricos reduzem alucinações e respostas fora do escopo.

**Nuances:**  
- Contexto demais sem foco pode dispersar a IA: priorize o essencial.  
- Prefira contextos que ajudem a IA a entender a finalidade da resposta.

---

### 🟣 **R - Referência**

As **Referências** guiam o estilo, formato ou modelo da saída.  
**Como atuar:**  
✅ Inclua exemplos, links, amostras de estilo (ex.: "Use o estilo da Wikipédia", "Siga o modelo anexo").  
✅ Refira-se a materiais que a IA possa imitar ou se inspirar.  
✅ Se não tiver referência externa, cite atributos desejados: “Clareza como em manuais da Apple”.

**Nuances:**  
- Referências muito genéricas não ajudam (ex.: “como um bom artigo”).  
- Quanto mais próximo do resultado esperado, melhor a referência.

---

### 🟣 **E - Expectativa**

A **Expectativa** define o formato e a natureza da resposta.  
**Como atuar:**  
✅ Explique o formato: “Resposta em bullet points”, “Código em Python”, “Texto persuasivo”.  
✅ Limite o tamanho se necessário: “Até 100 palavras”, “Resumo em 3 parágrafos”.  
✅ Alinhe com o uso final: “Para apresentação”, “Para email formal”.

**Nuances:**  
- Sem expectativa clara, a IA tende a adivinhar o que você quer.  
- Combine expectativa com contexto e tarefa para máxima precisão.

---

### 🟣 **I - Iteração**

A **Iteração** trata de como você ajusta e refina o resultado.  
**Como atuar:**  
✅ Avalie a resposta e peça ajustes: “Agora adicione exemplos”, “Torne mais direto”.  
✅ Planeje ciclos de revisão: peça para explicar raciocínio (Chain-of-Thought), comparar versões (Tree-of-Thought).  
✅ Use o histórico para refinamento incremental.

**Nuances:**  
- Iteração bem-feita transforma um bom prompt em um excelente.  
- Repetição sem critério pode gerar deriva (desvio do foco).

---

## 🔑 Dicas Gerais para TCREI

✅ **Comece simples, refine com iteração.**  
✅ **Use todos os elementos do TCREI quando a tarefa for complexa.**  
✅ **Seja consistente: um prompt consistente gera melhores respostas.**  
✅ **Teste versões do prompt: compare saídas e ajuste.**

---

## ✅ Conclusão

Trabalhar com TCREI é como liderar um projeto: você define o escopo (T), o cenário (C), as inspirações (R), o formato final (E) e conduz melhorias (I). Quanto mais atenção ao detalhe em cada etapa, melhor o resultado da IA.
