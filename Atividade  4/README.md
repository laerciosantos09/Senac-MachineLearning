# Atividade 4 - Curvas ROC e AUC

## 👨‍💻 Autor

**Laércio Santos**  
Pós-graduação em Inteligência Artificial - Centro Universitário SENAC


## Análise de Predição de Doenças Cardíacas (Framingham Heart Study)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/Respostas_Atividade_4.ipynb)

**Link direto:** [Abrir no Google Colab](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/Respostas_Atividade_4.ipynb)

**Objetivo:** Construir e comparar classificadores para prever o risco de doença cardíaca em 10 anos (TenYearCHD)

---

## 📊 Dataset

O dataset utilizado é o **Framingham Heart Study**, contendo 4.238 registros e 16 variáveis relacionadas a fatores de risco cardiovascular.

| Variável | Descrição |
|----------|-----------|
| male | Sexo (1 = masculino, 0 = feminino) |
| age | Idade do paciente |
| education | Nível de educação |
| currentSmoker | Fumante atual (1 = sim) |
| cigsPerDay | Cigarros por dia |
| BPMeds | Uso de medicamentos para pressão |
| prevalentStroke | Histórico de AVC |
| prevalentHyp | Hipertensão prevalente |
| diabetes | Diabetes |
| totChol | Colesterol total |
| sysBP | Pressão arterial sistólica |
| diaBP | Pressão arterial diastólica |
| BMI | Índice de massa corporal |
| heartRate | Frequência cardíaca |
| glucose | Nível de glicose |
| **TenYearCHD** | **Risco de doença cardíaca em 10 anos (variável alvo)** |

### ⚠️ Desbalanceamento do Dataset
- **84.8%** - Sem doença cardíaca (classe 0)
- **15.2%** - Com doença cardíaca (classe 1)

---

## 📝 Respostas das Tarefas

### **Tarefa 1: Classificador de Regressão Logística**

Foi criado um classificador de Regressão Logística utilizando **todas as 15 variáveis** do dataset para prever a variável `TenYearCHD`.

#### Resultados do Modelo:

| Métrica | Valor |
|---------|-------|
| **Acurácia** | 0.8475 |
| **Precisão** | 0.4815 |
| **Recall** | 0.0674 |
| **F1-Score** | 0.1182 |
| **AUC-ROC** | 0.7020 |

#### Relatório de Classificação:
```
              precision    recall  f1-score   support

     Sem CHD       0.86      0.99      0.92      1079
     Com CHD       0.48      0.07      0.12       193

    accuracy                           0.85      1272
```

#### Variáveis Mais Importantes (por coeficiente):

[![Coeficientes da Regressão Logística](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%20%204/coeficientes_regressao_logistica.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/coeficientes_regressao_logistica.png)

#### Correlação das Variáveis com TenYearCHD:

[![Correlação das Variáveis](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%20%204/correlacao_variaveis.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/correlacao_variaveis.png)

---

### **Tarefa 2: Combinações de Variáveis para o Melhor Classificador**

Foram testados **5 conjuntos diferentes de variáveis** para identificar a melhor combinação:

| Conjunto | Variáveis | AUC-ROC |
|----------|-----------|---------|
| **Conjunto 1 (Correlação)** ✅ | age, sysBP, prevalentHyp, glucose, male, cigsPerDay | **0.7066** |
| Conjunto 3 (Fatores de Risco) | age, male, currentSmoker, cigsPerDay, prevalentHyp, diabetes, totChol, sysBP, BMI | 0.7055 |
| Conjunto 4 (Coeficientes) | age, male, sysBP, glucose, prevalentStroke, cigsPerDay | 0.7046 |
| Todas as Variáveis | 15 variáveis | 0.7020 |
| Conjunto 5 (Minimalista) | age, sysBP, male, glucose | 0.6997 |
| Conjunto 2 (Clínicas) | age, sysBP, diaBP, totChol, BMI, heartRate, glucose | 0.6765 |

#### 🏆 Melhor Combinação: **Conjunto 1 (Correlação)**
- **Variáveis:** `age`, `sysBP`, `prevalentHyp`, `glucose`, `male`, `cigsPerDay`
- **AUC-ROC:** 0.7066

> **Conclusão:** O modelo com apenas 6 variáveis baseadas em correlação superou o modelo com todas as 15 variáveis, demonstrando que a seleção adequada de features pode melhorar a performance.

---

### **Tarefa 3: Curvas ROC e AUC**

As curvas ROC foram construídas para comparar visualmente o desempenho dos diferentes conjuntos de variáveis.

#### Curvas ROC - Comparação de Conjuntos de Variáveis:

[![Curvas ROC - Conjuntos de Variáveis](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%20%204/curvas_roc_conjuntos.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/curvas_roc_conjuntos.png)

#### Comparação de AUC por Conjunto:

[![Comparação AUC](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%20%204/comparacao_auc_conjuntos.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/comparacao_auc_conjuntos.png)

---

### **Tarefa 4: Comparação com SVM e KNN**

Os três classificadores foram comparados utilizando todas as variáveis:

#### Tabela Comparativa Final:

| Classificador | Acurácia | Precisão | Recall | F1-Score | AUC-ROC |
|---------------|----------|----------|--------|----------|---------|
| **Regressão Logística** ✅ | 0.8475 | 0.4815 | 0.0674 | 0.1182 | **0.7020** |
| KNN (K=21) | 0.8467 | 0.4167 | 0.0259 | 0.0488 | 0.6618 |
| SVM (RBF) | 0.8498 | 0.6250 | 0.0259 | 0.0498 | 0.5747 |

#### Otimização do KNN:
Foram testados diferentes valores de K:

| K | AUC-ROC |
|---|---------|
| 3 | 0.5789 |
| 5 | 0.6180 |
| 7 | 0.6254 |
| 9 | 0.6350 |
| 11 | 0.6488 |
| 15 | 0.6556 |
| **21** | **0.6618** |

#### Curvas ROC - Comparação entre Classificadores:

[![Curvas ROC - Classificadores](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%20%204/curvas_roc_classificadores.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/curvas_roc_classificadores.png)

#### Matrizes de Confusão:

[![Matrizes de Confusão](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%20%204/matrizes_confusao.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/matrizes_confusao.png)

#### Comparação de Métricas:

[![Comparação de Métricas](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%20%204/comparacao_metricas.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/comparacao_metricas.png)

#### Ranking Final:

[![Ranking Final](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%20%204/ranking_final.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/ranking_final.png)
---

## 📈 Conclusões

### 1. Melhor Classificador (baseado em AUC-ROC):
**Regressão Logística** com AUC-ROC = **0.7020**

### 2. Análise do Desbalanceamento:
- Dataset original possui apenas **15.2%** de casos positivos (CHD)
- Isso afeta principalmente o **Recall** dos classificadores
- A métrica **AUC-ROC** é mais robusta para datasets desbalanceados

### 3. Comparação dos Classificadores:
| Classificador | AUC | Características |
|---------------|-----|-----------------|
| Regressão Logística | 0.7020 | Interpretável, rápido |
| KNN (K=21) | 0.6618 | Simples, baseado em distância |
| SVM (RBF) | 0.5747 | Bom para dados não-lineares |

### 4. Variáveis Mais Importantes (Correlação com TenYearCHD):
1. **age:** 0.2253
2. **sysBP:** 0.2164
3. **prevalentHyp:** 0.1776
4. **diaBP:** 0.1453
5. **glucose:** 0.1255

### 5. Recomendações:
- ✅ Para **interpretabilidade**: Regressão Logística
- 🔄 Considerar técnicas de **balanceamento** (SMOTE, undersampling)
- ⚙️ **Ajuste de hiperparâmetros** pode melhorar resultados
- 📊 Para este dataset, **menos variáveis** podem gerar melhor AUC

---

## 📁 Arquivos do Projeto

| Arquivo | Descrição |
|---------|-----------|
| [Respostas_Atividade_4.ipynb](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/Respostas_Atividade_4.ipynb) | Notebook com código completo |
| [framingham.csv](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%20%204/framingham.csv) | Dataset utilizado |

---

## 🚀 Como Executar

1. Clique no botão **"Open in Colab"** no topo deste README
2. Execute todas as células sequencialmente
3. Os gráficos e resultados serão gerados automaticamente

---



