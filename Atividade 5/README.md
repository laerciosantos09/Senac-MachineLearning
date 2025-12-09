
# Atividade 5 - Classificação de Notas de Banco

Este documento apresenta a resolução da Atividade 5, utilizando Python e a biblioteca Scikit-Learn para treinar e avaliar modelos de Machine Learning na tarefa de classificação de autenticidade de notas de banco.

## 👨‍💻 Autor

**Laércio Santos**  
Pós-graduação em Inteligência Artificial - Centro Universitário SENAC


 [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%205/Respostas%20Atividade%205.ipynb)

**Link direto:** [Abrir no Google Colab](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%205/Respostas%20Atividade%205.ipynb)

## 1. Criação dos Classificadores

Foram criados dois tipos de classificadores para este problema:

* **Naive Bayes:** Utilizou-se o algoritmo `GaussianNB`, adequado para dados com distribuição normal.
* **Regressão Logística:** Utilizou-se o algoritmo `LogisticRegression`, integrado em um pipeline com `StandardScaler` para padronização dos dados, o que favorece o desempenho deste modelo.

## 2. Validação Cruzada e Seleção de Modelos

A validação cruzada foi aplicada para avaliar a robustez dos modelos e selecionar os melhores hiperparâmetros.

* **Estratégia:** Foi utilizado o `StratifiedKFold` com 10 dobras (folds), garantindo que a proporção de classes fosse mantida em cada divisão de treino e teste.
* **Naive Bayes:** Obteve uma **acurácia média de 83.54%** (+/- 4.19%) na validação cruzada.
* **Regressão Logística:** Foi submetida ao `GridSearchCV` para otimização dos hiperparâmetros `C` (força da regularização) e `solver`.
    * **Melhores Parâmetros:** `{'logisticregression__C': 100, 'logisticregression__solver': 'liblinear'}`.
    * **Melhor Acurácia Média:** **98.96%**.

**Conclusão da Seleção:** A Regressão Logística apresentou desempenho superior na validação cruzada e foi escolhida como o modelo final.

## 3. Matriz de Confusão

A matriz de confusão foi gerada utilizando o modelo vencedor (Regressão Logística) nos dados de teste reservados (30% do dataset original).

[![Matriz de Confusão](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%205/MatrizConfusao.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%205/MatrizConfusao.png)

**Análise dos Resultados no Teste:**
* O modelo atingiu uma **acurácia de 99%** no conjunto de teste.
* Observa-se um excelente desempenho em ambas as classes (0 e 1), com precisão e recall próximos de 1.00.

## 4. Salvamento do Modelo

O melhor modelo treinado (Regressão Logística) foi serializado e salvo em disco utilizando a biblioteca `pickle`.

* **Nome do Arquivo:** `modelo_banknote_final.pkl`.
* **Teste de Carregamento:** O modelo foi carregado e testado novamente, confirmando a acurácia de 99.03%.

---
*Este relatório foi gerado com base na execução do notebook `Respostas Atividade 5.ipynb`.*
