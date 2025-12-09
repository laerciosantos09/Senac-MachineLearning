# Exercícios - Regressão Linear Univariada

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

# 📝 EXERCÍCIO 1 - Portland House Prices

**Objetivo:** Treinar modelos lineares na base Portland_housePrices.csv utilizando apenas um dos atributos preditores.

## Resultados Obtidos

| Atributo | R² | RSS | Coeficiente |
|----------|-----|-----|-------------|
| **Tamanho** | **0.7310** | **193,464,477,600.71** | 134.53 |
| Quartos | 0.1956 | 578,535,325,112.52 | 72,669.65 |

## Visualização dos Modelos

![Exercício 1 - Comparação Tamanho vs Quartos](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/images/ex1_comparacao.png)

![Minha Imagem](./imagens/ex1_comparacao.png)

---

## Respostas - Exercício 1

### P1. Observando visualmente o modelo, qual atributo parece mais razoável?

**Resposta:** O atributo **TAMANHO** parece visualmente mais razoável porque:

- Os pontos de dados estão **mais próximos da linha de regressão**
- Há uma **relação linear mais clara** e evidente entre tamanho e preço
- A **dispersão dos resíduos é menor** e mais uniforme ao redor da reta
- No gráfico de "Quartos vs Preço", os pontos estão muito dispersos verticalmente para cada valor de quarto, indicando que o número de quartos sozinho não explica bem a variação no preço

### P2. O que foi aprendido com tamanho ou com número de quartos?

**Resposta:**

**Com Tamanho:**
- **Coeficiente aprendido: 134.53** → Para cada pé² adicional, o preço aumenta aproximadamente $134,53
- O modelo aprendeu uma relação forte e consistente: casas maiores custam mais
- R² = 0.73 indica que **73% da variação no preço é explicada pelo tamanho**

**Com Quartos:**
- **Coeficiente aprendido: 72,669.65** → Para cada quarto adicional, o preço aumenta aproximadamente $72,669
- O modelo aprendeu uma relação fraca: mais quartos tendem a aumentar o preço, mas com muita variabilidade
- R² = 0.20 indica que **apenas 20% da variação no preço é explicada pelo número de quartos**
- O atributo "quartos" é discreto (poucos valores únicos: 1-5), o que dificulta o ajuste linear

### P3. O RSS e R² corroboram suas impressões observando o modelo?

**Resposta:** **SIM**, as métricas corroboram completamente a análise visual:

| Métrica | Tamanho | Quartos | Interpretação |
|---------|---------|---------|---------------|
| **R²** | 0.7310 ✅ | 0.1956 | Tamanho explica ~3.7x mais variância |
| **RSS** | 193 bi ✅ | 578 bi | Tamanho tem ~3x menos erro total |

- **R² do Tamanho é muito MAIOR (0.73 vs 0.20):** Confirma que o tamanho explica uma proporção significativamente maior da variância do preço
- **RSS do Tamanho é muito MENOR:** Confirma que as previsões baseadas no tamanho são muito mais precisas (menor soma dos erros quadrados)

**Conclusão:** O modelo com **TAMANHO** é claramente superior ao modelo com **QUARTOS** para prever o preço das casas em Portland.

---

# 📝 EXERCÍCIO 2 - Advertising

**Objetivo:** Treinar modelos lineares na base Advertising.csv utilizando apenas um dos atributos preditores.

## Resultados Obtidos

| Atributo | R² | RSS | Coeficiente |
|----------|-----|-----|-------------|
| **TV** | **0.6119** | **2,102.53** | 0.0475 |
| Radio | 0.3320 | 3,618.48 | 0.2025 |
| Newspaper | 0.0521 | 5,134.80 | 0.0547 |

## Visualização dos Modelos

![Exercício 2 - Comparação TV, Radio e Newspaper](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/images/ex2_comparacao.png)

![Exercício 2 - Gráfico de Barras Comparativo](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/images/ex2_barras.png)

---

## Respostas - Exercício 2

### P1. Observando visualmente o modelo, qual atributo parece mais razoável?

**Resposta:** Visualmente, o atributo **TV** parece mais razoável porque:

- Os pontos seguem um **padrão linear mais claro** e definido
- A **dispersão ao redor da linha de regressão é menor**
- Há uma **tendência crescente mais evidente**: quanto maior o investimento em TV, maiores as vendas

**Análise visual dos três atributos:**
- **TV:** Relação linear clara, pontos bem agrupados ao redor da reta
- **Radio:** Alguma relação positiva visível, mas com dispersão maior
- **Newspaper:** Relação muito fraca, pontos extremamente dispersos, quase sem padrão linear

### P2. O que foi aprendido com TV, radio ou newspaper?

**Resposta:**

**Com TV:**
- **Coeficiente: 0.0475** → Para cada $1.000 investidos em TV, as vendas aumentam ~47,5 unidades
- R² = 0.61 → **61% da variação nas vendas é explicada pelo investimento em TV**
- Aprendizado: TV tem **forte influência positiva** nas vendas

**Com Radio:**
- **Coeficiente: 0.2025** → Para cada $1.000 investidos em Radio, as vendas aumentam ~202,5 unidades
- R² = 0.33 → **33% da variação nas vendas é explicada pelo investimento em Radio**
- Aprendizado: Radio tem **influência moderada** nas vendas
- Nota: O coeficiente maior não significa melhor modelo - a variabilidade é muito alta

**Com Newspaper:**
- **Coeficiente: 0.0547** → Para cada $1.000 investidos em Newspaper, as vendas aumentam ~54,7 unidades
- R² = 0.05 → **Apenas 5% da variação nas vendas é explicada pelo investimento em Newspaper**
- Aprendizado: Newspaper tem **influência muito fraca/quase nula** nas vendas

### P3. Qual dos modelos é melhor? Como você chegou a esta conclusão?

**Resposta:** O modelo com **TV** é claramente o melhor.

**Metodologia utilizada para chegar a esta conclusão:**

1. **Análise do R² (Coeficiente de Determinação):**
   - TV: R² = 0.6119 → **Melhor** (explica 61% da variância)
   - Radio: R² = 0.3320 → Intermediário (explica 33%)
   - Newspaper: R² = 0.0521 → **Pior** (explica apenas 5%)

2. **Análise do RSS (Residual Sum of Squares):**
   - TV: RSS = 2,102 → **Melhor** (menor erro total)
   - Radio: RSS = 3,618 → Intermediário
   - Newspaper: RSS = 5,134 → **Pior** (maior erro total)

3. **Análise Visual:**
   - TV apresenta os pontos mais próximos da linha de regressão

**Ranking Final: TV > Radio > Newspaper**

**Conclusão:** Para prever vendas usando apenas um atributo, o investimento em **TV** é o preditor mais confiável e preciso.

---

# 📝 EXERCÍCIO 3 - Comparação LR vs KNN com Train/Test Split

**Objetivo:** 
1. Comparar os resultados das duas regressões com a implementação do KNN-Regressor
2. Utilizar partições de treino e teste para avaliar os modelos

## Resultados Obtidos

### Portland House Prices (Tamanho → Preço)

| Modelo | R² Dataset Completo | R² Treino | R² Teste |
|--------|---------------------|-----------|----------|
| **Linear Regression** | 0.7310 | 0.7665 | **0.5850** |
| KNN (k=3) | 0.7886 | 0.7366 | 0.1771 |
| KNN (k=5) | 0.7612 | 0.6878 | 0.3057 |
| KNN (k=7) | 0.6988 | 0.6368 | 0.3145 |

### Advertising (TV → Sales)

| Modelo | R² Dataset Completo | R² Treino | R² Teste |
|--------|---------------------|-----------|----------|
| **Linear Regression** | 0.6119 | 0.5736 | **0.6714** |
| KNN (k=3) | 0.7558 | 0.6634 | 0.5977 |
| KNN (k=5) | 0.6632 | 0.6228 | 0.6394 |
| KNN (k=7) | 0.6441 | 0.6015 | 0.6653 |

## Visualização dos Resultados

![Exercício 3 - Comparação R² por Modelo](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/images/ex3_comparacao_r2.png)

![Exercício 3 - Treino vs Teste](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%202/images/ex3_treino_teste.png)

---

## Respostas - Exercício 3

### Comparação: Regressão Linear vs KNN-Regressor

**Regressão Linear:**
- Modelo **paramétrico e simples**
- Assume uma **relação linear** entre as variáveis
- Menos propenso a overfitting em dados com relação aproximadamente linear
- **Mais estável** entre treino e teste

**KNN (K-Nearest Neighbors):**
- Modelo **não-paramétrico e mais flexível**
- Pode capturar **relações não-lineares**
- Mais propenso a **overfitting** (especialmente com k pequeno)
- O valor de K influencia o trade-off entre viés e variância:
  - k pequeno → baixo viés, alta variância (overfitting)
  - k grande → alto viés, baixa variância (underfitting)

**Observações dos resultados:**
- Para dados com relação aproximadamente linear (como estes), a **Regressão Linear geralmente tem desempenho igual ou melhor** que KNN no teste
- KNN com k=3 tem R² alto no dataset completo (0.79 em Portland), mas **generaliza muito mal** (R² = 0.18 no teste)
- A Regressão Linear é mais consistente entre treino e teste

---

### Item 1. Comparar os resultados na partição de treino e teste

**Resposta:**

**Observação geral:** O desempenho no **treino tende a ser igual ou melhor** que no teste, porque:
- O modelo foi **ajustado/otimizado** nos dados de treino
- Os dados de teste são **"novos"** para o modelo

**Análise Portland:**

| Modelo | R² Treino | R² Teste | Diferença | Interpretação |
|--------|-----------|----------|-----------|---------------|
| LR | 0.77 | 0.59 | -0.18 | Boa generalização |
| KNN(k=3) | 0.74 | 0.18 | **-0.56** | Overfitting severo! |
| KNN(k=5) | 0.69 | 0.31 | -0.38 | Overfitting |
| KNN(k=7) | 0.64 | 0.31 | -0.33 | Overfitting |

**Análise Advertising:**

| Modelo | R² Treino | R² Teste | Diferença | Interpretação |
|--------|-----------|----------|-----------|---------------|
| LR | 0.57 | 0.67 | +0.10 | Excelente generalização |
| KNN(k=3) | 0.66 | 0.60 | -0.06 | Boa generalização |
| KNN(k=5) | 0.62 | 0.64 | +0.02 | Excelente generalização |
| KNN(k=7) | 0.60 | 0.67 | +0.07 | Excelente generalização |

**Conclusões:**
- **Grande diferença treino-teste indica overfitting** (modelo memorizou os dados de treino)
- No dataset Portland (menor, 47 amostras), o overfitting é mais severo
- No dataset Advertising (maior, 200 amostras), os modelos generalizam melhor
- **Regressão Linear é mais estável** e menos propensa a overfitting

---

### Item 2. Comparar desempenho com a regressão na qual não foi feita a separação entre treino e teste

#### Item 2.1. Você acha que o desempenho deveria ser melhor ou pior nesse caso?

**Resposta:** O desempenho no **dataset completo** (sem separação) tende a ser **"MELHOR" (R² mais alto)**, mas isso é uma **avaliação ENGANOSA e OTIMISTA**.

**Por quê?**

1. **O modelo é avaliado nos mesmos dados em que foi treinado**
   - É como um aluno estudar apenas as respostas da prova e depois fazer a mesma prova
   - O modelo pode ter "decorado" os dados ao invés de aprender padrões generalizáveis

2. **Evidência nos resultados:**
   - Portland LR: Dataset completo (0.73) > Teste (0.59)
   - Portland KNN(k=3): Dataset completo (0.79) >> Teste (0.18) ← **Diferença enorme!**

3. **O R² no dataset completo superestima a capacidade real do modelo**
   - Não reflete como o modelo se comportará com dados nunca vistos
   - Pode mascarar problemas de overfitting

#### Item 2.2. É possível dizer que os modelos treinados no dataset completo generalizam?

**Resposta:** **NÃO é possível afirmar com confiança** que modelos treinados no dataset completo generalizam.

**Motivos:**

1. **Sem separação treino/teste, não há como medir a capacidade de generalização**
   - Generalização = capacidade de fazer boas previsões em dados NOVOS
   - Se usamos todos os dados para treinar E avaliar, nunca vemos dados "novos"

2. **O modelo pode estar sofrendo overfitting sem que saibamos**
   - Exemplo: KNN(k=3) em Portland tem R² = 0.79 no dataset completo
   - Mas quando testamos em dados novos: R² = 0.18 (péssimo!)
   - Sem o split, nunca descobriríamos esse problema

3. **A métrica no dataset completo é ENVIESADA**
   - Sempre será igual ou melhor que a métrica real de generalização
   - Dá uma falsa sensação de que o modelo é bom

**Conclusão Final:**

> **A prática correta é SEMPRE usar partições de treino/teste (ou validação cruzada) para avaliar modelos de forma honesta e estimar como eles se comportarão com dados nunca vistos antes.**

---

## 📊 Resumo Geral dos 3 Exercícios

| Exercício | Dataset | Melhor Atributo/Modelo | Conclusão Principal |
|-----------|---------|------------------------|---------------------|
| 1 | Portland | **Tamanho** | R² = 0.73 (3.7x melhor que Quartos) |
| 2 | Advertising | **TV** | R² = 0.61 (TV > Radio > Newspaper) |
| 3 | Ambos | **Linear Regression** | Train/test split é essencial para avaliar generalização |

## 🎯 Aprendizados-Chave

1. **R² alto** = modelo explica bem a variância dos dados
2. **RSS baixo** = previsões mais próximas dos valores reais
3. **Sempre usar train/test split** para avaliação honesta
4. **Diferença grande treino-teste** = possível overfitting
5. **Mais dados** = menos overfitting e melhor generalização
6. **Regressão Linear** é mais estável que KNN para relações lineares

---

## 🛠️ Tecnologias Utilizadas

- Python 3
- Pandas
- NumPy
- Matplotlib
- Scikit-learn (LinearRegression, KNeighborsRegressor, train_test_split)

---

## 👤 Autor

**Laércio Santos**

Pós-graduação em Inteligência Artificial - Centro Universitário SENAC
