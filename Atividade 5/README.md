
# Atividade 5 - Identificando Notas Falsas com Inteligência Artificial

Este documento resume a Atividade 5. O objetivo aqui foi ensinar o computador a olhar para características de uma nota de dinheiro e dizer automaticamente se ela é **verdadeira** ou **falsa**.

## 👨‍💻 Autor

**Laércio Santos**  
Pós-graduação em Inteligência Artificial - Centro Universitário SENAC


 [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%205/Respostas%20Atividade%205.ipynb)

**Link direto:** [Abrir no Google Colab](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%205/Respostas%20Atividade%205.ipynb)


## 1. Criando os "Robôs" (Classificadores)

* **Naive Bayes:** Um modelo baseado em probabilidades estatísticas simples.
* **Regressão Logística:** Um modelo matemático muito usado para separar coisas em duas categorias (neste caso: nota falsa vs. nota verdadeira).

## 2. A Bateria de Testes (Validação Cruzada)

Não basta treinar o modelo uma vez e confiar. Para ter certeza de que o computador aprendeu mesmo (e não apenas decorou as respostas), usamos uma técnica chamada **Validação Cruzada**.

* **Como funciona:** Dividimos os dados em 10 partes. Treinamos com 9 partes e testamos na parte que sobrou. Repetimos isso 10 vezes mudando as partes. É como fazer 10 provas diferentes para garantir que o aluno é bom mesmo.

  
* **O Resultado:** O modelo de **Regressão Logística** foi o campeão. Ele teve uma nota média de quase **99%**, superando o outro modelo. Nós também fizemos alguns ajustes finos (chamados de *hiperparâmetros*) para garantir que ele funcionasse na sua potência máxima.


## 3. O "Boletim" Final (Matriz de Confusão)

Depois de escolher o melhor modelo, fizemos um teste final com dados que ele nunca tinha visto antes. O resultado é mostrado na imagem abaixo, chamada de Matriz de Confusão. Ela mostra quantos acertos e erros o modelo teve.

[![Matriz de Confusão](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%205/MatrizConfusao.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%205/MatrizConfusao.png)

**O que isso significa?**
* O modelo teve uma **taxa de acerto (acurácia) de 99%**.
* Ele praticamente não confundiu notas falsas com verdadeiras. O desempenho foi excelente.

## 4. Guardando o Cérebro do Modelo (Pickle)

Como o modelo funcionou muito bem, nós o "salvamos" em um arquivo.

* **O que foi feito:** Usamos uma ferramenta chamada `pickle` para salvar todo o aprendizado do computador em um arquivo chamado `modelo_banknote_final.pkl`.
* **Para que serve:** Isso permite que a gente use essa inteligência artificial no futuro sem precisar treinar tudo do zero novamente. É como salvar o progresso de um jogo.

---
*Relatório gerado a partir do notebook `Respostas Atividade 5.ipynb`.*
