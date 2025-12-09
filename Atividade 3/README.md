# Respostas dos Exercícios de Regressão Linear

## 👤 Autor

**Laércio Santos**

Pós-graduação em Inteligência Artificial - Centro Universitário SENAC


## 🚀 Executar no Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%203/RespostasAtividade3.ipynb)

**Link direto:** [Abrir no Google Colab](https://colab.research.google.com/github/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%203/RespostasAtividade3.ipynb)


## Exercício 1: Testando os "Motores" de Aprendizado
**Testamos duas formas diferentes (algoritmos) de ensinar o computador a prever vendas.**

### 1. O resultado muda se eu rodar o treino várias vezes?
* **Método Clássico (LinearRegression):** **Não.** É como uma calculadora: se você somar 2 + 2, sempre dará 4. Ele usa uma fórmula matemática exata, então o resultado é sempre idêntico.
* **Método de Tentativa e Erro (SGDRegressor):** **Sim.** Esse método aprende por "tentativa e erro". Ele começa chutando valores aleatórios e vai ajustando. Por isso, cada vez que você roda, o resultado final pode ser um pouquinho diferente, dependendo de onde ele começou os chutes.

### 2. Os dois métodos chegaram na mesma conclusão?
**R:** Eles chegaram em resultados **quase idênticos**.
* O método clássico encontra a resposta matematicamente perfeita.
* O método de tentativa e erro chega muito, muito perto dessa resposta perfeita (se dermos tempo suficiente para ele aprender).

---

## Exercício 2: Usando todas as informações (TV, Rádio e Jornal)
**Agora, tentamos prever as vendas usando todos os canais de publicidade ao mesmo tempo.**

### 1. O modelo fica melhor se usarmos todos os dados?
**R: Sim, melhora muito.**
* Quando olhamos para TV, Rádio e Jornal juntos, conseguimos explicar quase **90%** do comportamento das vendas.
* Se olhássemos apenas para a TV, explicaríamos apenas 60%. Ou seja: quanto mais informação relevante, melhor a previsão.

### 2. Tem alguma informação inútil que poderíamos jogar fora?
**R: Sim, o "Jornal" (Newspaper).**
* Descobrimos que investir em Jornal não ajuda a prever as vendas se já soubermos quanto foi gasto em TV e Rádio. Se removermos a coluna "Jornal" da análise, a precisão do modelo continua praticamente a mesma (90%).

### 3. Qual método foi mais rápido para treinar?
**R:** Para essa planilha pequena (200 linhas), o **Método Clássico** foi mais rápido.
* O método de "tentativa e erro" (SGD) só vale a pena quando temos uma quantidade gigantesca de dados (milhões de linhas), onde a matemática do método clássico travaria o computador.

---

## Exercício 3: Verificando a qualidade da previsão
**Fizemos uma "auditoria" para ver onde o modelo está errando e quais variáveis são confiáveis.**

### 1. Onde o modelo erra? Existe um padrão nos erros?
**R:** O modelo é bom, mas **não é perfeito**.
* Ao analisar os erros (a diferença entre o que o modelo previu e o que realmente vendeu), notamos que existe um leve padrão (uma curva). Isso significa que a relação entre propaganda e vendas não é uma linha reta perfeita; existe alguma complexidade extra que nosso modelo simples não captou 100%, mas chegou perto.
* 
[![Plot de Resíduos](https://raw.githubusercontent.com/laerciosantos09/Senac-MachineLearning/main/Atividade%203/plot_residuos.png)](https://github.com/laerciosantos09/Senac-MachineLearning/blob/main/Atividade%203/plot_residuos.png)

### 2. Estatisticamente, quem são os "culpados" pelas vendas?
**R:**
* **TV e Rádio:** A estatística confirma com certeza absoluta que eles aumentam as vendas.
* **Jornal:** A estatística mostra que ele **não tem relevância**. É como se fosse "ruído" na comunicação.
* **Conclusão:** Podemos criar um modelo mais simples e eficiente usando apenas TV e Rádio, ignorando o Jornal.

---

## Exercício 4: As variáveis se copiam? (Multicolinearidade)
**Checamos se as variáveis são independentes ou se uma está "imitando" a outra.**

### 1. Existe redundância entre os canais de publicidade?
**R:** **Não, cada canal é independente.**
* Fizemos um teste chamado VIF e os resultados foram baixos (próximos de 1).
* Isso é ótimo! Significa que o gasto em TV não está "amarrado" ao gasto em Rádio. Eles são decisões separadas, o que torna mais fácil para o computador entender qual é a contribuição real de cada um para as vendas.
