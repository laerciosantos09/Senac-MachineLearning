# Exercícios - Regressão Linear Univariada


## 👤 Autor

**Laércio Santos**

Pós-graduação em Inteligência Artificial - Centro Universitário SENAC


## 🚀 Executar no Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%202/Solucao_Exercicios_Regressao_Linear.ipynb)

**Link direto:** [Abrir no Google Colab](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%202/Solucao_Exercicios_Regressao_Linear.ipynb)

---

## 📁 Fontes de Dados

| Dataset | Descrição | Link |
|---------|-----------|------|
| **Portland House Prices** | Preços de casas com tamanho e número de quartos (47 amostras) | [Portland_housePrices.csv](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/refs/heads/main/Atividade%202/Portland_housePrices.csv) |
| **Advertising** | Dados de publicidade (TV, Radio, Newspaper) e vendas (200 amostras) | [Advertising.csv](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/refs/heads/main/Atividade%202/Advertising.csv) |

---

# 📝 EXERCÍCIO 1 - Preço de Casas (Portland)

**O Desafio:** Descobrir o que influencia mais no preço final de um imóvel: o **tamanho** (área) ou o **número de quartos**.

## Resultados Simplificados

| Atributo | Precisão do Modelo (R²) | Margem de Erro (RSS) | Impacto no Preço |
|----------|-----|-----|-------------|
| **Tamanho** | **73% (Alta)** | **Menor Erro** | +$134 por pé² |
| Quartos | 20% (Baixa) | Maior Erro | +$72.669 por quarto |

## Visualização dos Modelos

[![Exercício 1 - Comparação Tamanho vs Quartos](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/ex1_comparacao.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%202/ex1_comparacao.png)

---

## Respostas - Exercício 1

### P1. Olhando o gráfico, qual característica faz mais sentido?

**Resposta:** O **TAMANHO** é visualmente o vencedor.
* Note como os pontos (casas) seguem uma linha crescente bem definida: casa maior, preço maior.
* Já no gráfico de quartos, os pontos estão muito espalhados. Existem casas com poucos quartos que são caras e casas com muitos quartos que são baratas, o que confunde o modelo.

### P2. O que aprendemos com cada característica?

**Resposta:**

**Com Tamanho (O Vencedor):**
* **Regra de Ouro:** Para cada unidade de espaço a mais, o preço sobe cerca de **$134**.
* O modelo confia que **73%** da variação de preço vem do tamanho. É uma aposta segura.

**Com Quartos (O Perdedor):**
* **Regra Fraca:** O modelo tenta dizer que cada quarto aumenta o preço em ~$72 mil, mas ele erra muito.
* Apenas **20%** do preço é explicado pelos quartos. É uma aposta arriscada.

### P3. Os números confirmam o visual?

**Resposta:** **SIM**. Os números comprovam o que vimos no gráfico.
* A precisão (R²) do Tamanho é quase **4 vezes maior** que a de Quartos.
* O erro acumulado (RSS) do Tamanho é muito menor.
* **Conclusão:** Para avaliar uma casa nesta região, use a régua, não conte as portas.

---

# 📝 EXERCÍCIO 2 - Investimento em Propaganda

**O Desafio:** Temos dados de vendas baseados em investimentos em TV, Rádio e Jornal. Qual mídia traz mais retorno e previsibilidade?

## Resultados Simplificados

| Atributo | Precisão (R²) | Impacto nas Vendas | Classificação |
|----------|-----|-------------|---|
| **TV** | **61% (Boa)** | +47 vendas a cada $1k | 🥇 O Melhor |
| Radio | 33% (Média) | +202 vendas a cada $1k | 🥈 Instável |
| Newspaper | 5% (Péssima) | +54 vendas a cada $1k | 🥉 Irrelevante |

## Visualização dos Modelos

[![Exercício 2 - Comparação TV, Radio e Newspaper](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/ex2_comparacao.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%202/ex2_comparacao.png)

[![Exercício 2 - Gráfico de Barras Comparativo](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/ex2_barras.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%202/ex2_barras.png)

---

## Respostas - Exercício 2

### P1. Olhando o gráfico, onde o dinheiro rende mais?

**Resposta:** Na **TV**.
* O gráfico da TV mostra uma "escada" clara: quanto mais se investe, mais se vende.
* O Rádio tem muito ruído (pontos espalhados).
* O Jornal parece uma nuvem aleatória, sem padrão nenhum.

### P2. O que aprendemos sobre cada mídia?

**Resposta:**

* **TV (Segurança):** Explica **61%** das vendas. É o investimento mais previsível.
* **Rádio (Risco):** Explica **33%**. Parece dar muito retorno por dólar investido, mas é instável.
* **Jornal (Desperdício):** Explica apenas **5%**. Basicamente, anunciar no jornal não garante venda nenhuma neste cenário.

### P3. Qual é o melhor modelo?

**Resposta:** O modelo baseado em **TV** é o campeão.

**Ranking de Confiabilidade:**
1.  **TV:** Maior precisão, menor erro.
2.  **Rádio:** Precisão mediana.
3.  **Jornal:** Precisão quase nula.

**Conclusão:** Se tiver verba para apenas um canal, aposte na TV.

---

# 📝 EXERCÍCIO 3 - O Teste da "Decoreba" (Treino vs Teste)

**O Desafio:** Comparar dois "cérebros" artificiais (Regressão Linear e KNN) para ver quem realmente aprende e quem apenas decora os dados.

* **Regressão Linear:** Tenta traçar uma reta simples (tendência).
* **KNN:** Tenta copiar os vizinhos mais próximos.

## Resultados Obtidos

### Preço de Casas (Portland)

| Modelo | Nota no Estudo (Treino) | Nota na Prova (Teste) | Veredito |
|--------|---------------------|-----------|----------|
| **Regressão Linear** | 76% | **58%** | **Aprovado (Honesto)** |
| KNN (k=3) | 73% | 17% | Reprovado (Decoreba) |

### Propaganda (Advertising)

| Modelo | Nota no Estudo (Treino) | Nota na Prova (Teste) | Veredito |
|--------|---------------------|-----------|----------|
| **Regressão Linear** | 57% | **67%** | **Aprovado (Excelente)** |
| KNN (k=3) | 66% | 59% | Aprovado |

## Visualização dos Resultados


[![Exercício 3 - Comparação R² por Modelo](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/ex3_comparacao_r2.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%202/ex3_comparacao_r2.png)

[![Exercício 3 - Treino vs Teste](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/ex3_treino_teste.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%202/ex3_treino_teste.png)


---

## Respostas - Exercício 3

### Diferença entre os "Cérebros"

* **Regressão Linear (O Aluno Esforçado):** Tenta entender a lógica geral (a tendência). É mais simples, mas mais robusto quando vê dados novos.
* **KNN (O Aluno que Cola):** Tenta adivinhar a resposta olhando para os exemplos vizinhos. Se ele "colar" de poucos vizinhos (k=3), ele acerta muito no treino, mas erra feio na prova real.

### Item 1. Por que separar Treino e Teste?

**Resposta:**

É como separar o **livro de exercícios** da **prova final**.
* No caso das Casas em Portland, o modelo **KNN** foi desmascarado. Ele teve nota alta no treino (74%), mas tirou nota 18% na prova (Teste). Isso é **Overfitting** (superajuste/decoreba).
* A **Regressão Linear** manteve notas mais próximas, provando ser mais confiável.

### Item 2. E se usássemos todos os dados sem separar?

**Resposta:** Seria uma **ilusão**.
* O desempenho pareceria incrível (notas altas), mas seria falso.
* Estaríamos dando a prova com as mesmas perguntas que o aluno já viu.
* **Conclusão:** Sem separar dados de Teste, não temos como saber se a IA vai funcionar no mundo real.

---

## 📊 Resumo Final para Gestores

| Lição | Explicação |
|-----------|---------------------|
| **Tamanho Importa** | Para casas, área construída é o melhor indicador de preço. |
| **TV Vende** | Para este cliente, TV é o investimento de marketing mais seguro. |
| **Não se Iluda** | Sempre exija testes com dados "novos" para validar qualquer IA. |
| **Simplicidade** | Muitas vezes, o modelo mais simples (Regressão Linear) bate o mais complexo. |

---

## 🛠️ Tecnologias Utilizadas

- Python 3
- Pandas & NumPy (Cálculos)
- Matplotlib (Gráficos)
- Scikit-learn (Inteligência Artificial)

---
